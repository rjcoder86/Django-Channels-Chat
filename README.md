# Django Channels Chat Application

## Overview

This project is a chat application built using Django Channels, WebSockets, and RabbitMQ. It allows real-time communication between users in chat rooms and direct chat.

## Features

- Real-time chat functionality
- Separate chat rooms
- Direct user-to-user chat
- Message differentiation for current user

## Setup Instructions

### Prerequisites

- Python 3.6+
- Django 3.1+
- Channels
- RabbitMQ

### Installation

1. **Clone the Repository**

   ```sh
   git clone https://github.com/rjcoder86/Django-Channels-Chat.git
   cd django-channels-chat
2. **Create a Virtual Environment**

    ```sh
    python3 -m venv env
    source env/bin/activate  # On Windows, use `env\Scripts\activate```
3. **Install Dependencies**

    ```sh
    pip install -r requirements.txt
4. **Set Up RabbitMQ**

- Install RabbitMQ:

#### On Windows
Download the RabbitMQ installer from the official RabbitMQ website and follow the instructions.

- Start RabbitMQ:

#### On Windows
Run the RabbitMQ Server from the Start Menu or using the command prompt:

    
    rabbitmq-server.bat

- Enable RabbitMQ management plugin to access the web    
management console:

    ```sh
    sudo rabbitmq-plugins enable rabbitmq_management```
The management interface can be accessed at http://localhost:15672. The default username and password are both guest.

5. **Configure Django Settings**

Add the following configuration to your settings.py:

    CHANNEL_LAYERS = {
        'default': {
            'BACKEND': 'channels_rabbitmq.core.RabbitmqChannelLayer',
            'CONFIG': {
                'hosts': [('localhost', 5672)],
            },
        },
    }

6. **Apply Migrations**

    ```sh
    python manage.py migrate```
7. **Create Superusers**

    ```sh
    python manage.py createsuperuser
    python manage.py createsuperuser
Follow the prompts to create two superusers. These users will be used to chat with each other.

8. **Run the Development Server**

    ```sh
    python manage.py runserver
    ```

### **Usage**

1. **Access the Admin Interface**

Go to http://localhost:8000/admin and log in using the superuser credentials.

2. **Create Chat Rooms**

Use the admin interface to create chat rooms if needed.

3. **Access Chat Rooms**

Directly access or create a chat room by navigating to:

```bash
http://localhost:8000/chat/room_name
```
Replace room_name with your desired chat room name.

4. **Access Direct Chat**

Directly access or create a direct chat room by navigating to:

```bash
http://localhost:8000/direct_chat/room_name
```
Replace room_name with your desired direct chat room name.

#### File Structure
```
    ├── chatapp/
    │   ├── templates/
    │   │   ├── chat.html
    │   │   ├── direct_chat.html
    │   ├── admin.py
    │   ├── consumers.py
    │   ├── models.py
    │   ├── routing.py
    │   ├── tests.py
    │   ├── urls.py
    │   └── views.py
    ├── config/
    │   ├── settings.py
    │   ├── urls.py
    │   ├── asgi.py
    │   ├── wsgi.py
    ├── manage.py
    ├── README.md
    ├── requirements.txt
```

#### RabbitMQ Management Interface
Access the RabbitMQ management interface at http://localhost:15672. The default username and password are both guest.
