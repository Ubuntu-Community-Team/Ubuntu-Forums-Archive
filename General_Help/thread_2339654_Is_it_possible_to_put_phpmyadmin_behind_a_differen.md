---
title: "Is it possible to put phpmyadmin behind a different IP on the same server?"
date: 2016-10-11
forum: General Help
---

### Post by kjetil-fleten on 2016-10-11
Hi

We have a server running php on AWS. We would like to make sure that phpmyadmin is available from a single IP only, while the rest of the services can be accessed from different IP's. Is it possible to put phpmyadmin behind a different IP on the same server, if we make multiple IP's on the server ?

---

### Post by SeijiSensei on 2016-10-11
Yes, just specify the IP in the <VirtualHost> stanza in Apache.

```

<VirtualHost 10.10.10.10:80>
ServerName phpmyadmin.example.com
DocumentRoot /path/to/phpmyadmin
[stuff]
</VirtualHost>

<VirtualHost 10.10.10.11:80>
ServerName somesite.example.com
[stuff]
</VirtualHost>

<VirtualHost 10.10.10.11:80>
ServerName anothersite.example.com
[stuff]
</VirtualHost>

```

---

