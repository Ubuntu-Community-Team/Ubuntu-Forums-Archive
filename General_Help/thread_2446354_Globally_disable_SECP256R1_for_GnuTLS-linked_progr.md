---
title: "Globally disable SECP256R1 for GnuTLS-linked programs?"
date: 2020-06-29
forum: General Help
---

### Post by boekhold2 on 2020-06-29
Hi,

Ubuntu 20.04

I have a very strange issue that seems to be specific to the geographical location I'm located in. GnuTLS-linked programs have trouble connecting to many sites. Also see [https://gitlab.com/gnutls/gnutls/-/issues/990](https://gitlab.com/gnutls/gnutls/-/issues/990) for a long discussion on this. The short of the story is that any connection attempt that tries to use the SECP256R1 elliptic curve encryption fails. Unfortunately those programs include APT and GIT, which means for example that mono-project.com as an apt repository doesn't work, and I'm unable to clone any github repo.

The gnutls-cli program has command line options that let you control which encryption methods are attempted by gnutls-cli, e.g.:

gnutls-cli --priority=NORMAL:-GROUP-SECP256R1 github.com

works, but:

[FONT=monospace]gnutls-cli github.com[/FONT]

Does not.

Does anybody know of a way to globally/system-wide adjust the *priority *that GnuTLS uses? I have found some references to possible gnutls configuration files, but that support seems to be dependent on specific compilation options, and I don't know which options are used for the Ubuntu 20.04 package. Also, I found update-crypto-policy, which I hoped would be able to do this, but I've not been able to figure out how to actually use it.

Rgds

---

### Post by boekhold2 on 2020-06-29
Hmmm,

Doesn't look like the Ubuntu libgnutls30 package has a default priority file location compiled in ([https://gnutls.org/manual/html_node/System_002dwide-configuration-of-the-library.html#:~:text=The%20location%20of%20the%20default,can%20be%20queried%20using%20gnutls_get_system_config_file.](https://gnutls.org/manual/html_node/System_002dwide-configuration-of-the-library.html#:~:text=The%20location%20of%20the%20default,can%20be%20queried%20using%20gnutls_get_system_config_file.)). I downloaded the Ubuntu source packages, and there is no reference to "GNUTLS_SYSTEM_PRIORITY_FILE", nor to the "with_system_priority_file" configure option.

Also, I very much doubt that the update-crypto-policies tool has any impact on libgnutls30: again the source package doesn't have any reference to "/etc/crypto-policies" whatsoever.

I'll try to set GNUTLS_SYSTEM_PRIORITY_FILE through /etc/profile and see what happens...

---

### Post by norobro on 2020-06-29
I know nothing about this but I perused the docs and the following seems to work.
[https://www.gnutls.org/manual/html_node/System_002dwide-configuration-of-the-library.html#System_002dwide-configuration-of-the-library](https://www.gnutls.org/manual/html_node/System_002dwide-configuration-of-the-library.html#System_002dwide-configuration-of-the-library)
[https://www.gnutls.org/manual/html_node/Disabling-algorithms-and-protocols.html#Disabling-algorithms-and-protocols](https://www.gnutls.org/manual/html_node/Disabling-algorithms-and-protocols.html#Disabling-algorithms-and-protocols)

Results before creating config file:```
$ gnutls-cli github.com
...
[SIZE=2][FONT=monospace][SIZE=1][COLOR=#000000]- Status: The certificate is trusted.  [/COLOR]
- Description: (TLS1.3-X.509)-(ECDHE-[COLOR=#ff0000]SECP256R1[/COLOR])-(RSA-PSS-RSAE-SHA256)-(AES-128-GCM)[/SIZE]
[/FONT][/SIZE]...
```

After:```
[FONT=monospace][COLOR=#000000]$ [SIZE=1]cat /etc/gnutls/config  [/SIZE][/COLOR][SIZE=1]
[overrides]
tls-disabled-group=GROUP-SECP256R1[/SIZE]

[/FONT]$ gnutls-cli github.com
[SIZE=1][FONT=monospace][COLOR=#000000]...
- Status: The certificate is trusted.  [/COLOR]
- Description: (TLS1.3-X.509)-(ECDHE-[COLOR=#ff0000]X25519[/COLOR])-(RSA-PSS-RSAE-SHA256)-(AES-128-GCM)
...[/FONT][/SIZE]
```HTH


Edit: 

The default config file is defined in config.ac: [https://github.com/gnutls/gnutls/blob/master/configure.ac#L849](https://github.com/gnutls/gnutls/blob/master/configure.ac#L849)

When configure is executed it generates a config.h file which contains:```
/* The system-wide gnutls configuration file */
#define SYSTEM_PRIORITY_FILE "/etc/gnutls/config"
```

---

### Post by boekhold2 on 2020-06-30
I've got GIT working by creating the following file

```

# /etc/gnutls/config
[overrides]
tls-disabled-group = group-secp256r1

```

However this doesn't work for apt/apt-get. If I run:

```

export GNUTLS_DEBUG_LEVEL=9
apt update

```

I'm getting a different kind of exception from gnutls:

```

gnutls[3]: ASSERT: ../../lib/record.c[check_session_status]:1649
gnutls[3]: ASSERT: ../../lib/record.c[gnutls_bye]:324
Err:14 https://download.mono-project.com/repo/ubuntu stable-focal Release                                                     
  Could not handshake: A TLS fatal alert has been received. [IP: 152.199.19.161 443]

```

Will keep investigating...

---

### Post by ActionParsnip on 2020-06-30
Could make a BASH alias in ~/.bashrc

```

alias gnutls-cli='gnutls-cli --priority=NORMAL:-GROUP-SECP256R1'

```

---

### Post by norobro on 2020-06-30
With ECDHE-SECP256R1 disabled in /etc/gnutls/config the mono-project server used ECDHE-SECP384R1 ```
$ gnutls-cli mono-project.com
. . .
- Description: (TLS1.2-X.509)-(ECDHE-SECP384R1)-(RSA-SHA256)-(AES-256-GCM)
. . .
```So I disabled secp384r1 and the server fell back to using RSA.```
$ cat /etc/gnutls/config 
[overrides]
tls-disabled-group=GROUP-SECP256R1
tls-disabled-group=GROUP-SECP384R1


$ gnutls-cli mono-progect.com
. . .
- Description: (TLS1.2-X.509)-(RSA)-(AES-256-GCM)
. . .
```


I don't have a problem using secp256r1 so I can't test this but perhaps disabling secp384R1 also will allow apt to download from that repository.

---

