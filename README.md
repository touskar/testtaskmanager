
# **Projet CRUD : Gestion des Tâches Étendue**

## **Description**  
Créer une **API RESTful** avec **AdonisJS** pour la gestion des tâches (**TODO list**) avec des relations **Lucid ORM**. L'API doit permettre :  
- D'**assigner des tâches** à des utilisateurs.  
- De **lier des tâches** à des projets et des étiquettes.  
- De **récupérer les tâches** par utilisateur et par projet.

## **Modèles à Implémenter**

### **1. User**  
Le modèle `User` représente les utilisateurs.

| Champ      | Type      | Description                     |
|------------|-----------|---------------------------------|
| id         | Integer   | Identifiant unique              |
| email      | String    | Email de l'utilisateur          |
| password   | String    | Mot de passe (haché)            |
| created_at | Timestamp | Date de création                |
| updated_at | Timestamp | Dernière mise à jour            |

**Relations** :  
- `hasMany` : Un utilisateur a plusieurs tâches.  
- `manyToMany` : Un utilisateur peut appartenir à plusieurs projets.

### **2. Task**  
Le modèle `Task` représente les tâches à accomplir.

| Champ         | Type      | Description                    |
|---------------|-----------|--------------------------------|
| id            | Integer   | Identifiant unique             |
| title         | String    | Titre de la tâche              |
| description   | Text      | Description optionnelle        |
| completed     | Boolean   | Statut de la tâche (terminée)  |
| due_date      | DateTime  | Date d'échéance                |
| user_id       | Integer   | Clé étrangère vers `User`      |
| project_id    | Integer   | Clé étrangère vers `Project`   |
| created_at    | Timestamp | Date de création               |
| updated_at    | Timestamp | Dernière mise à jour           |

**Relations** :  
- `belongsTo` : Une tâche appartient à un utilisateur.  
- `belongsTo` : Une tâche appartient à un projet.  
- `manyToMany` : Une tâche peut avoir plusieurs étiquettes.

### **3. Project**  
Le modèle `Project` représente les projets.

| Champ         | Type      | Description                    |
|---------------|-----------|--------------------------------|
| id            | Integer   | Identifiant unique             |
| name          | String    | Nom du projet                  |
| description   | Text      | Description du projet          |
| created_at    | Timestamp | Date de création               |
| updated_at    | Timestamp | Dernière mise à jour           |

**Relations** :  
- `hasMany` : Un projet a plusieurs tâches.  
- `manyToMany` : Un projet peut inclure plusieurs utilisateurs.

### **4. Tag**  
Le modèle `Tag` représente des étiquettes pour catégoriser les tâches.

| Champ         | Type      | Description                    |
|---------------|-----------|--------------------------------|
| id            | Integer   | Identifiant unique             |
| name          | String    | Nom de l'étiquette             |
| created_at    | Timestamp | Date de création               |
| updated_at    | Timestamp | Dernière mise à jour           |

**Relations** :  
- `manyToMany` : Une étiquette peut être assignée à plusieurs tâches.

## **Endpoints à Implémenter**

| Méthode | Endpoint                   | Fonctionnalité                        | Authentification |
|---------|----------------------------|--------------------------------------|------------------|
| POST    | `/tasks`                   | Créer une tâche                      |  ✅               |
| GET     | `/tasks`                   | Récupérer toutes les tâches          | ✅               |
| GET     | `/tasks/user/:id`          | Voir les tâches d'un utilisateur      | ✅               |
| PUT     | `/tasks/:id`               | Mettre à jour une tâche               | ✅               |
| DELETE  | `/tasks/:id`               | Supprimer une tâche                   | ✅               |
| POST    | `/projects`                | Créer un projet                      | ✅               |
| GET     | `/projects/:id/tasks`      | Récupérer les tâches d'un projet      | ✅               |
| POST    | `/tasks/:id/tags`          | Assigner des tags à une tâche         | ✅               |
| GET     | `/tasks/:id/tags`          | Récupérer les tags d'une tâche        | ✅               |
| POST    | `/projects/:id/users`      | Assigner des utilisateurs à un projet | ✅               |
| GET     | `/projects/:id/users`      | Récupérer les utilisateurs d'un projet| ✅               |

## **Contraintes Techniques**

- Utiliser **AdonisJS v5+**.
- Base de données : SQLite, MySQL ou PostgreSQL.
- Respecter les conventions des **routes RESTful**.
- Créer et utiliser des **relations** entre les modèles.
- Mettre en place l'authentification via **JWT**.
- Ajouter des **validations** pour sécuriser les entrées.

## **Livrables Attendus**

1. Code source complet du projet.
2. Migrations et seeders pour la base de données.
3. Documentation des endpoints (via **Postman** https://www.postman.com/).
