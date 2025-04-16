# Ferdium Server Self-Hosting

This repository contains configuration files to easily self-host the Ferdium server using Docker.

## What is Ferdium?

Ferdium is a free, open-source alternative to Franz and Ferdi, allowing you to combine various messaging services into one application. The Ferdium server provides synchronization of services, workspaces, and settings across multiple devices.

## Requirements

- Docker
- Docker Compose

## Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/ferdium-selfhost.git
   cd ferdium-selfhost
   ```

2. Edit the `docker-compose.yml` file to configure your environment variables:
   - Change `APP_URL` to your domain or IP address if accessible from the internet
   - Set `APP_KEY` to a random string (important for security)
   - Adjust registration settings as needed (`IS_REGISTRATION_ENABLED`, etc.)

3. Start the Ferdium server:
   ```bash
   docker-compose up -d
   ```

4. Access the Ferdium server at `http://localhost:3333`

## Configuration Options

Key environment variables in the `docker-compose.yml`:

| Variable | Description | Default |
|----------|-------------|---------|
| APP_URL | URL where your server is accessible | http://localhost:3333 |
| IS_CREATION_ENABLED | Enable creation of new accounts | true |
| IS_DASHBOARD_ENABLED | Enable the dashboard | true |
| IS_REGISTRATION_ENABLED | Enable registration of new users | true |
| CONNECT_WITH_FRANZ | Allow connection with Franz | false |
| APP_KEY | Random string used for encryption | CHANGE_THIS_TO_RANDOM_STRING |

## Data Persistence

The following directories are persisted as volumes:
- `./data`: Application data
- `./config`: Configuration files
- `./database`: SQLite database

## Updating

To update the Ferdium server to the latest version:

```bash
docker-compose pull
docker-compose down
docker-compose up -d
```

## Connecting Ferdium Client

1. Download the Ferdium client from [https://ferdium.org/](https://ferdium.org/)
2. When starting Ferdium for the first time, click "Change server"
3. Enter your server URL (e.g., `http://localhost:3333`)
4. Create an account or sign in

## Security Considerations

If exposing your Ferdium server to the internet:
- Use HTTPS (through a reverse proxy like Nginx or Traefik)
- Set a strong APP_KEY
- Consider limiting registration after creating your account(s)

## Troubleshooting

- Check logs: `docker-compose logs -f`
- Ensure ports are not blocked by firewall
- Check that Docker has sufficient permissions to create and manage the volumes

