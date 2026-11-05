# Gestion des Réclamations & Avis — Client JavaFX

Application de bureau **JavaFX** pour gérer les **réclamations**, les **avis** sur les articles et les **réponses** aux clients. Elle partage la base MySQL du module web Symfony [ClaimManagement](https://github.com/yosradab/ClaimManagement).

Projet académique réalisé à ESPRIT (projet intégré PIDEV, volet Java).

## Fonctionnalités

### Espace utilisateur (`EspaceUser`)
- **Réclamer un service** : formulaire de réclamation avec ajout d'une capture d'écran
- **Noter un article** : ajout d'un avis avec une note

### Gestion des réclamations
- Liste, ajout, modification et suppression des réclamations
- **Changement de statut** (`StatusReclamation`) avec **notification du client par e-mail** (JavaMail, SMTP)

### Gestion des avis
- Liste, ajout, modification et suppression des avis
- Filtrage des avis par article

### Réponses
- Gestion des réponses envoyées aux réclamations (`GestionReponse`)

## Stack technique

| Élément | Technologie |
|---|---|
| Langage | Java 8+ |
| Interface | JavaFX + FXML (Scene Builder) |
| Accès aux données | JDBC (singleton `DataSource`) |
| Base de données | MySQL, partagée avec l'application Symfony |
| E-mail | JavaMail (SMTP Gmail, port 587, STARTTLS) |

## Architecture

```
Entités       Reclamation, Avis, Reponse
Services      ServiceReclamation, ServiceAvis, ServiceReponse   (CRUD JDBC)
Contrôleurs   *Controller.java                                  (logique des écrans)
Vues          *.fxml                                            (écrans JavaFX)
Utilitaires   MailService                                       (envoi d'e-mails)
Main.java     Point d'entrée, ouvre GestionReclamation.fxml
```

## Lancer le projet

1. Importer les sources dans un projet JavaFX (NetBeans, IntelliJ ou Eclipse) avec le SDK JavaFX et le connecteur **MySQL Connector/J**.
2. Ajouter une classe `Tools.DataSource` (singleton JDBC, non incluse dans ce dépôt) pointant vers la base MySQL qui contient les tables `reclamation`, `avis` et `reponse`.
3. Renseigner l'adresse et le mot de passe d'application SMTP dans `MailService.java`.
4. Lancer `Main.java`.

## Auteur

**Yosra Dab** — Ingénieure logiciel Full Stack · [Portfolio](https://yosradab.vercel.app) · [GitHub](https://github.com/yosradab) · [LinkedIn](https://linkedin.com/in/yosradab)
