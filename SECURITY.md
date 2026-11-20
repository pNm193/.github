TapCep Security Policy

1. Purpose

This policy establishes security expectations and procedures for the TapCep repository, its application source code, database integrations, external services, dependencies, and development environment.

TapCep is a PHP-based application designed to perform Brazilian CEP (postal-code) lookups using a local MySQL database and an external lookup service.

The project recognizes the importance of protecting application integrity, database credentials, user-submitted information, and the availability and reliability of external integrations.

2. Scope

This policy applies to:

* PHP application code and server-side processing.
* MySQL database connections and queries.
* CEP input validation and processing.
* External República Virtual web service integrations.
* Google Maps integrations.
* JavaScript, jQuery, jQTouch, and third-party libraries.
* Application caching and manifest functionality.
* Repository contents, configuration files, and deployment procedures.
* Automated development, testing, and release processes, where implemented.

3. Vulnerability Reporting

Security vulnerabilities should be reported privately.

Do not publicly disclose exploitable vulnerabilities through GitHub issues, pull requests, or discussions before maintainers have had an opportunity to investigate.

Use GitHub Private Vulnerability Reporting if enabled for this repository.

Reports should include:

* A description of the vulnerability.
* The affected file, component, or application functionality.
* Steps to reproduce the issue.
* Potential impact.
* Relevant supporting evidence.
* Suggested remediation, if available.

Never include passwords, database credentials, authentication tokens, private keys, or confidential personal information in a vulnerability report.

4. Application Security Requirements

4.1 Input Validation

All user-submitted CEP values must be validated on the server.

Requirements include:

* Accept only numeric CEP input.
* Enforce the expected eight-digit CEP format.
* Reject malformed, excessively long, or unexpected input.
* Normalize input before database queries.
* Never rely exclusively on client-side validation.

4.2 Database Security

Database access must follow secure development practices.

Requirements include:

* Use parameterized queries or prepared statements.
* Avoid deprecated database interfaces such as PHP’s legacy mysql_* functions.
* Restrict database accounts to the permissions required by the application.
* Protect database connection credentials.
* Prevent database errors and internal configuration details from being exposed to application users.
* Validate database identifiers separately from user-provided values.

4.3 External Service Integrations

External services, including República Virtual and Google Maps, must be treated as third-party dependencies.

Requirements include:

* Prefer HTTPS connections.
* Validate external service responses.
* Implement appropriate connection timeouts and error handling.
* Avoid exposing sensitive information through external requests.
* Prevent untrusted external responses from being treated as executable content.
* Document external service dependencies and availability limitations.

4.4 Client-Side Security

JavaScript and browser-facing components must follow secure coding practices.

Requirements include:

* Prevent cross-site scripting (XSS).
* Safely render returned address information.
* Avoid inserting untrusted data into HTML.
* Use secure external resource connections.
* Review third-party JavaScript libraries for known vulnerabilities.
* Avoid unnecessary browser permissions and data collection.

5. Configuration and Secret Management

Database credentials and other sensitive configuration information must not be committed to the public repository.

The following practices are required:

* Keep production configuration files outside source control.
* Maintain placeholder-only sample configuration files.
* Exclude sensitive configuration files through .gitignore.
* Never hardcode passwords, API keys, or access tokens.
* Rotate credentials if exposure is suspected.
* Review repository history if credentials are accidentally committed.

6. Dependency and Supply Chain Security

Project maintainers should periodically review third-party libraries and services.

Particular attention should be given to:

* PHP dependencies and runtime compatibility.
* Legacy jQuery and jQTouch components.
* External JavaScript libraries.
* Database-related dependencies.
* Third-party APIs and web services.
* Software updates and unsupported components.

Known vulnerabilities should be evaluated and addressed according to severity and practical remediation requirements.

7. GitHub Repository Security

The repository should use available GitHub security features, including:

* Private vulnerability reporting.
* Dependabot alerts where supported.
* Secret scanning where available.
* Push protection where available.
* Protected default branches.
* Pull request review requirements appropriate to the project.
* Restricted repository and workflow permissions.
* Review of third-party GitHub Actions before use.

GitHub Actions should use least-privilege permissions and should not expose repository secrets to untrusted pull request code.

8. Error Handling and Logging

Application errors should be handled without exposing:

* Database credentials.
* SQL statements containing sensitive information.
* Internal server paths.
* Authentication information.
* Detailed infrastructure configuration.

Production systems should use controlled server-side logging.

Logs should not unnecessarily retain sensitive user-submitted information.

9. Vulnerability Assessment and Remediation

Reported vulnerabilities should be evaluated according to:

* Severity.
* Exploitability.
* Affected application components.
* Potential database exposure.
* Potential compromise of application integrity.
* Impact on availability.
* Third-party service dependencies.

Critical and high-severity vulnerabilities should receive priority.

Security fixes should be tested before deployment whenever reasonably possible.

10. Responsible Disclosure

Security researchers and contributors are encouraged to report vulnerabilities privately and allow reasonable time for investigation and remediation.

Maintainers should coordinate disclosure with reporting researchers when appropriate.

Public security advisories should provide affected-version information, remediation guidance, and relevant mitigations without unnecessarily exposing exploitable technical details.

11. Supported Versions

TapCep is a legacy application. Security support and compatibility should be evaluated according to actively maintained versions.

No assumption should be made that older releases, dependencies, or deployment configurations receive ongoing security maintenance.

12. Policy Maintenance

This policy should be reviewed periodically and updated as TapCep’s architecture, dependencies, database implementation, and deployment practices evolve.

Repository: pNm193/tapcep

Policy File: SECURITY.md

Policy Status: Proposed

Last Reviewed: November 20, 2026
