# Rundeck Plugin Build ZIP

A modernized, secure Gradle build system for creating Rundeck plugins in ZIP format.

## Features

- **Security Focused**: Uses latest Gradle 8.10.2 with security best practices
- **Modern Gradle**: Uses plugins block, Provider API, and configuration avoidance
- **CVE Scanning**: Automated vulnerability scanning via Snyk and GitHub Actions
- **Secure Publishing**: HTTPS-only repositories and proper POM metadata
- **Reproducible Builds**: Consistent output with timestamp preservation disabled

## Usage

1. Include this as a shared build script in your Rundeck plugin projects
2. Create a `gradle.properties` file with your plugin details:
   ```properties
   archivesBaseName=my-plugin
   version=1.0.0
   pluginName=My Rundeck Plugin
   pluginDescription=Description of my plugin
   sopsCopyright=Your Name
   sopsUrl=https://github.com/your-org/your-plugin
   ```
3. Create the required directory structure:
   - `resources/` - Plugin resources
   - `contents/` - Plugin content files
   - `plugin.yaml` - Plugin metadata (supports token replacement)

## build-zip

A modernized Gradle build system for creating Rundeck plugins in ZIP format. This shared build script provides standardized packaging for Rundeck plugins across the rundeck-plugins organization.

## Features

- **Modern Gradle 8.10.2**: Uses the latest stable Gradle version to avoid known CVEs
- **Security Hardened**: Includes security configurations and dependency verification support
- **Reproducible Builds**: Ensures consistent build outputs
- **Maven Publishing**: Supports publishing to GitHub Packages with secure authentication
- **Token Replacement**: Processes `plugin.yaml` with configurable tokens

## Usage

1. Include this repository as a Git submodule or copy the build files
2. Create a `gradle.properties` file with your plugin configuration:
   ```properties
   archivesBaseName=your-plugin-name
   version=1.0.0
   pluginName=Your Plugin Name
   pluginDescription=Description of your plugin
   sopsCopyright=Your Organization
   sopsUrl=https://github.com/your-org/your-plugin
   ```

3. Ensure your project structure includes:
   - `resources/` - Plugin resources
   - `contents/` - Plugin content files
   - `plugin.yaml` - Plugin metadata (tokens will be replaced)

4. Run the build:
   ```bash
   ./gradlew build
   ```

## Security

- Uses Gradle 8.10.2 to avoid known CVEs in older versions
- Supports dependency verification (run `./gradlew --write-verification-metadata sha256`)
- Configured for secure Maven publishing
- Includes Snyk security scanning via GitHub Actions
- Reproducible builds enabled

## Tasks

- `build` - Builds the plugin ZIP
- `pluginZip` - Creates the plugin ZIP archive
- `install` - Builds and installs to local Maven repository
- `publishToMavenLocal` - Publishes to local Maven repository
- `publish` - Publishes to configured repositories


```bash
# Build the plugin
./gradlew build

# Install to local Maven repository
./gradlew install

# Publish to remote repository
./gradlew publish
```

## Security

This build system includes several security measures:
- Uses latest stable Gradle version to avoid known CVEs
- HTTPS-only repository access
- Dependency vulnerability scanning integration
- Reproducible builds
- Secure credential management for publishing

## Requirements

- JDK 11 or higher
- Gradle 8.10.2+ (included via wrapper)
