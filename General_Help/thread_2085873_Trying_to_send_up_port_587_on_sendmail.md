---
title: "Trying to send up port 587 on sendmail"
date: 2012-11-19
forum: General Help
---

### Post by pinan on 2012-11-19
I have a private email server, normally I used squirrelmail to access it, but I would like to use thunderbird. 

Thunderbird want access to port 587 if I use STARTLS.

The version of sendmail provided on Lubuntu 12.04, only provides access to port 587 using localhost.

I want access to domain-name 587, so I can use a laptop when working from a customer site.

It looks like all you should do is to remove the no_default_msa, and type make and reload the configs.
Doing this, generates a message about 'opendaemonsocket: deamon MSA: can not bind: Address already in use, sendmail then dies with a message about SMTP socket wedged: exit

SO does anybody known how to configure sendmail so that it will accept non localhost connections on port 587?
I have looked on the wider net, but most of the answers either do not work or are several years out of date!

---

### Post by smtp on 2012-12-10
The follwoing row from sendmail.mc:

DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea, Addr=127.0.0.1')dnl

Should become

DAEMON_OPTIONS(`Family=inet,  Name=MSP-v4, Port=submission, M=Ea')dnl

Good luck!

---

### Post by SeijiSensei on 2012-12-10
You also have to rebuild sendmail.cf and restart sendmail itself.  I usually use symbolic links in the /etc/mail directory like this:

```

cd /etc/mail
sudo m4 < sendmail-new.mc > sendmail-new.cf
sudo mv sendmail.cf sendmail-old.cf
sudo ln -s sendmail-new.cf sendmail.cf
sudo service sendmail restart

```

Then if something goes wrong it's easy to revert to sendmail-old.cf just by repointing the symlink.

---

