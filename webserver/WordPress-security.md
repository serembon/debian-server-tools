# Blocking WordPress attack vectors

### Compromise from hosting provider

- Choose an enterprise ready server provider (e.g. [UpCloud](https://www.upcloud.com/register/?promo=U29Q8S))
- Secure control panel access: 2FA, login notification
- Secure API (IP whitelist)
- Subscribe to status updates
- [Protect computers](/Onboarding.md#secure-browser-in-an-ephemeral-cloud-instance)
  used for logging in (HitmanPro.Alert)

### Compromise through server software

- Use modern server software (OS, web server, PHP version, in-memory cache, database)
- Hide server software version
- Don't install multiple websites on a server / separate by OS user
- Subscribe to OS security updates

### Server-side

- HTTPS websites receive less attacks: force HTTPS ([HSTS](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Strict-Transport-Security))
- Block known hostile networks ([myattackers-ipset](https://github.com/szepeviktor/debian-server-tools/tree/master/security/myattackers-ipsets))
- Preventively block vulnerability scanners ([WordPress Fail2ban](https://github.com/szepeviktor/wordpress-fail2ban))
- Restrict access to core, theme and plugin files and directories ([wordpress.inc.conf](/webserver/apache-conf-available/wordpress.inc.conf))
- Disable file upload to the server
- Source code integrity check ([hourly](https://github.com/szepeviktor/debian-server-tools/blob/master/monitoring/tripwire-fake.sh))
- Alert on source code change ([hourly](https://github.com/szepeviktor/debian-server-tools/blob/master/monitoring/siteprotection.sh))
- Have daily offsite [backup](https://github.com/szepeviktor/debian-server-tools/tree/master/backup)
- Keep backups for one week

### Application

- Delete unused plugins and themes and demo content
- Audit plugins and themes (source code) - prefer authors providing enterprise services
- Install an [auditing plugin](https://wordpress.org/plugins/wp-user-activity/)
- Disable file editing
- Block on WordPress security events ([WordPress Fail2ban](https://github.com/szepeviktor/wordpress-fail2ban))
- Add SRI (Subresource Integrity) attributes to elements with foreign CDN content
- Content Security Policy (CSP) HTTP header
- Choose wisely if you decide on a [page builder](https://www.wpbeaverbuilder.com/?fla=2082)

### Authentication

- One administrator per site
- One user account per natural person
- Remove roles from unused accounts
- Disallow weak passwords
- Two-factor authentication
- Alert on foreign country logins (PHP `geoip_country_code_by_name()` or Apache mod_maxminddb)
- Analyse HTTP headers on login ([WordPress Fail2ban](https://github.com/szepeviktor/wordpress-fail2ban))
- Limit login attempts ([WordPress Fail2ban](https://github.com/szepeviktor/wordpress-fail2ban))

### Maintenance :wrench:

Have me on board: viktor@szepe.net

###### This page contains affiliate links
