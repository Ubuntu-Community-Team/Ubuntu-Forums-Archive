---
title: "Script Crontab"
date: 2007-04-04
forum: General Help
---

### Post by federer on 2007-04-04
hi !
Below my backup script.
I don´t know why but if you try to exec this script manually it works well...
But..in crontab file...it doesn´t...what´s the problem ?
It creates the file normally but not the normal file size..

#!/bin/sh
#Inicio do backup

cd /tmp/backup
DATA=`date +%Y-%m-%d-%H.%M-%a`
LISTA=$(cat /zona/backup/arqsdentro | grep ^\/ | sort | uniq)
tar -jcvf arquivos-"$DATA".tar.bz2 $LISTA -X /zona/backup/arqsfora

#Fim do backup

---

### Post by roelpeeters on 2007-04-04
What does your crontab look like? As what user is the script running? Are any startup running in your normal shell session that you need to run this script? Can you find any error messages in /var/log/daemon.log?

---

### Post by federer on 2007-04-04
Hey budy !!
My crontab is ok !...it calls my script normally...
the problem I think is in these lines:

LISTA=$(cat /zona/backup/arqsdentro | grep ^\/ | sort | uniq)
tar -jcvf arquivos-"$DATA".tar.bz2 $LISTA -X /zona/backup/arqsfora

do you have any idea ?




My crontab file:
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file.
# This file also has a username field, that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:

# m h dom mon dow user  command
17 *    * * *   root    run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.daily
47 6    * * 7   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.weekly
52 6    1 * *   root    test -x /usr/sbin/anacron || run-parts --report /etc/cron.monthly

# Esquema de backup Zona Nova
# ===========================

30 19   * * 0   root    rm -rf /temp/*
00 22   * * 1,2,3,4,5   root    /zona/backup/bkp-diario
00 22   * * 6   root    /zona/backup/bkp-semanal

# ===========================

---

### Post by roelpeeters on 2007-04-05
The only difference that I can see is that with crontab you have a different shell or environment than when you are running it normally. The following link may help you find the differences:

[http://blog.spikesource.com/crontab.htm](http://blog.spikesource.com/crontab.htm)

The other thing I thought of was that if you run your script twice from a normal shell, is the result always the same?

---

### Post by flightmaker on 2007-05-24
I was having trouble with this driving me nuts for the last few days.

I just found that if I send output from the script to a file it works, e,g,

0 23 * * 1-4 root /path/to/my/script/myscript > /path/filename

A friend who knows more about Linux than me suggested that because it normally tries to email the output of scripts to the user, but the mail program seems to be absent from this server, it's got nowhere to send the text and dies. Now that I've given the output an alternative destination, it's working.

---

