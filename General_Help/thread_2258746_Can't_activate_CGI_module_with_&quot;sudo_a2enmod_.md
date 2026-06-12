---
title: "Can't activate CGI module with &quot;sudo a2enmod cgi&quot;"
date: 2014-12-30
forum: General Help
---

### Post by DiogoSaraiva on 2014-12-30
when I issue  the command "sudo a2enmod cgi":

```

Your MPM seems to be threaded. Selecting cgid instead of cgi.
Enabling module cgid.
To activate the new configuration, you need to run:
service apache2 restart

```

I already reinstaled my Ubuntu...

it's Ubuntu Desktop 14.04.1 LTS 64bits


Why?


Can you help me please?


Thanks in advance...

---

### Post by Holger_Gehrke on 2014-12-30
Apache has more than one way to split itself into multiple handlers for connections. Those are called MPM (Multi Processing Module). You are using a thread based MPM. The cgi module can't work with that, so an equivalent module - cgid - gets activated. Details at [http://httpd.apache.org/docs/2.2/mod/mod_cgid.html](http://httpd.apache.org/docs/2.2/mod/mod_cgid.html)

---

### Post by DiogoSaraiva on 2014-12-30
> **Holger_Gehrke said:**
> You are using a thread based MPM
How, i don't setup this... I guess.

What I do wrong??

Please help me...

And now where I put my Cgi files?

/usr/lib/cgi-bin/ not found....

Thanks

---

### Post by DiogoSaraiva on 2014-12-30
Only thing I do:

Opened ports 443 and 80 to my ubuntu on my router and setup dynamical dns...

---

### Post by Holger_Gehrke on 2014-12-30
> **DiogoSaraiva said:**
> How, i don't setup this... I guess.

Meaning you didn't set up that machine or you didn't ask for the modern MPM ?
It gets installed by default, you only get another one if you ask for it.

> **DiogoSaraiva said:**
> 
And now where I put my Cgi files?

/usr/lib/cgi-bin/ not found....
Thanks

You can put your cgi-scripts wherever you want, you just have to change the Apache configuration accordingly. You **really** should read the documentation, it's **absolutely** necessary to know what you're doing if you're administrating your own server.

---

### Post by DiogoSaraiva on 2014-12-30
> **Holger_Gehrke said:**
> Meaning you didn't set up that machine or you didn't ask for the modern MPM ?


No i didn't set up yet only put ServerName 192.168.1.104 on top of apache2.conf

> **Holger_Gehrke said:**
> 
It gets installed by default, you only get another one if you ask for it.


How can I ask for it...
I installed apache2 with "sudo apt-get install apache2" or maybe "sudo apt-get install apache2 -y"

I will try:

"sudo dpkg-reconfigure apache2"

if not work:

"sudo apt-get --purge remove apache2" and reinstall with "sudo apt-get install apache2"

Thanks

---

### Post by DiogoSaraiva on 2014-12-30
Look: its says "[FONT=Menlo]Enabling module mpm_event."[/FONT]

```

[FONT=Menlo][COLOR=#34bd26]**diogosaraiva@Ubuntu**[/COLOR]:[COLOR=#5330e1]**~**[/COLOR]$ sudo apt-get install apache2[/FONT]
[FONT=Menlo]A ler as listas de pacotes... Pronto[/FONT]
[FONT=Menlo]A construir árvore de dependências       [/FONT]
[FONT=Menlo]A ler a informação de estado... Pronto[/FONT]
[FONT=Menlo]Pacotes sugeridos:[/FONT]
[FONT=Menlo]  apache2-doc apache2-suexec-pristine apache2-suexec-custom apache2-utils[/FONT]
[FONT=Menlo]Serão instalados os seguintes NOVOS pacotes:[/FONT]
[FONT=Menlo]  apache2[/FONT]
[FONT=Menlo]0 pacotes actualizados, 1 pacotes novos instalados, 0 a remover e 0 não actualizados.[/FONT]
[FONT=Menlo]É necessário obter 0 B/87,5 kB de arquivos.[/FONT]
[FONT=Menlo]Após esta operação, serão utilizados 473 kB adicionais de espaço em disco.[/FONT]
[FONT=Menlo]A seleccionar pacote anteriormente não seleccionado apache2.[/FONT]
[FONT=Menlo](A ler a base de dados ... 207864 ficheiros e directórios actualmente instalados.)[/FONT]
[FONT=Menlo]Preparing to unpack .../apache2_2.4.7-1ubuntu4.1_amd64.deb ...[/FONT]
[FONT=Menlo]Unpacking apache2 (2.4.7-1ubuntu4.1) ...[/FONT]
[FONT=Menlo]Processing triggers for man-db (2.6.7.1-1ubuntu1) ...[/FONT]
[FONT=Menlo]Processing triggers for ureadahead (0.100.0-16) ...[/FONT]
[FONT=Menlo]Processing triggers for ufw (0.34~rc-0ubuntu2) ...[/FONT]
[FONT=Menlo]A instalar apache2 (2.4.7-1ubuntu4.1) ...[/FONT]
[FONT=Menlo]Enabling module mpm_event.[/FONT]
[FONT=Menlo]Enabling module authz_core.[/FONT]
[FONT=Menlo]Enabling module authz_host.[/FONT]
[FONT=Menlo]Enabling module authn_core.[/FONT]
[FONT=Menlo]Enabling module auth_basic.[/FONT]
[FONT=Menlo]Enabling module access_compat.[/FONT]
[FONT=Menlo]Enabling module authn_file.[/FONT]
[FONT=Menlo]Enabling module authz_user.[/FONT]
[FONT=Menlo]Enabling module alias.[/FONT]
[FONT=Menlo]Enabling module dir.[/FONT]
[FONT=Menlo]Enabling module autoindex.[/FONT]
[FONT=Menlo]Enabling module env.[/FONT]
[FONT=Menlo]Enabling module mime.[/FONT]
[FONT=Menlo]Enabling module negotiation.[/FONT]
[FONT=Menlo]Enabling module setenvif.[/FONT]
[FONT=Menlo]Enabling module filter.[/FONT]
[FONT=Menlo]Enabling module deflate.[/FONT]
[FONT=Menlo]Enabling module status.[/FONT]
[FONT=Menlo]Enabling conf charset.[/FONT]
[FONT=Menlo]Enabling conf localized-error-pages.[/FONT]
[FONT=Menlo]Enabling conf other-vhosts-access-log.[/FONT]
[FONT=Menlo]Enabling conf security.[/FONT]
[FONT=Menlo]Enabling conf serve-cgi-bin.[/FONT]
[FONT=Menlo]Enabling site 000-default.[/FONT]
[FONT=Menlo] * Starting web server apache2                                                  AH00558: apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1. Set the 'ServerName' directive globally to suppress this message[/FONT]
[FONT=Menlo] * [/FONT]
[FONT=Menlo]Processing triggers for ureadahead (0.100.0-16) ...[/FONT]
[FONT=Menlo]Processing triggers for ufw (0.34~rc-0ubuntu2) ...[/FONT]
[COLOR=#34BD26][FONT=Menlo]**diogosaraiva@Ubuntu**[COLOR=#000000]:[/COLOR][COLOR=#5330e1]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT][/COLOR]
[COLOR=#000000]
```
[/COLOR]

---

### Post by DiogoSaraiva on 2014-12-30
Solved with 
```

sudo a2dismod mpm_event
sudo a2enmod mpm_prefork
sudo service apache2 restart

```
```

sudo a2enmod cgi

Enabling module cgi.
To activate the new configuration, you need to run:
service apache2 restart

```

Thanks for your time and sorry for be boring....
And happy new year

PS: I guess that is a bug... because i don't ask for mpm_event instead the old mpm_prefork, or maybe changed with a upgrade

---

