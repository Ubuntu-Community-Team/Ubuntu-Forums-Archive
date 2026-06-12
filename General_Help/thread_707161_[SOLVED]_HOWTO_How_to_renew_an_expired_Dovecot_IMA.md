---
title: "[SOLVED] HOWTO How to renew an expired Dovecot IMAP/POP3 SSL certificate"
date: 2008-02-25
forum: General Help
---

### Post by aoakley on 2008-02-25
By default in Ubuntu, the Dovecot IMAP/POP3 server installs a certificate which will expire after one year. Since you may still be using the same installation of Dovecot after a year, particularly if you are using an LTS version of Ubuntu such as Dapper or Hardy, you may wish to renew or replace this certificate with one that lasts for longer.

To renew/replace this certificate with one that doesn't expire for 5 years:

  sudo cp /etc/ssl/private/ssl-cert-snakeoil.key /etc/ssl/private/ssl-cert-snakeoil.key-backup
  sudo cp /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/certs/ssl-cert-snakeoil.pem-backup

  openssl genrsa -out server.key 1024
  openssl req -new -x509 -key server.key -out server.pem -days 1826

Two assumptions here:

1. This is domestic-grade security, suitable for a typical home server. If you require corporate or millitary-grade security, you really shouldn't be picking up tips from a forum post like this. Read up at: [www.openssl.org/docs](www.openssl.org/docs)

2. I have assumed that 5 years incorporates only 1 leap year. If you anticipate two leap years, use -days 1827 . If you anticipate no leap years, then... wow, Ubuntu is still in use in 2100! Yay team!

At this point it will ask for country code (eg. US or UK), province (eg. California or Gloucestershire), locality (eg. San Francisco or Tewkesbury), company name (you can leave this blank), section (you can leave this blank), common name (localhost, or your server's domain name, or your real name) and email address (root@localhost , or your email address). Then:

  sudo mv server.key /etc/ssl/private/ssl-cert-snakeoil.key
  sudo mv server.pem /etc/ssl/certs/ssl-cert-snakeoil.pem
  sudo /etc/init.d/dovecot restart

Close and re-open your email client, then check for new mail. You should be presented with the option to permanently accept the new key, and you should not encounter any certificate expiration messages for another five years.

Once you are happy that everything works, you may delete the backup copies of the original certificates (although it won't hurt to leave them in place):

  sudo rm /etc/ssl/private/ssl-cert-snakeoil.key-backup
  sudo rm /etc/ssl/certs/ssl-cert-snakeoil.pem-backup

I enncountered this expiration problem this morning, and it took a while to figure it out - most SSL howtos are for Apache. I'm posting this for my own reference as much as anything else!

---

### Post by angrydill on 2008-03-12
Thanks for all the info - I was pulling my hair out, and that helped a lot.

There was an additional thing I needed to do.  Dovecot had created it's original cert and key as /etc/ssl/certs/dovecot.pem and /etc/ssl/private/dovecot.pem, and still expected to those particular files.

I deleted them using:

rm /etc/ssl/certs/dovecot.pem
rm /etc/ssl/private/dovecot.pem

then replaced them with symbolic links to the newly-created files using:

ln -s /etc/ssl/certs/ssl-cert-snakeoil.pem /etc/ssl/certs/dovecot.pem      
ln -s /etc/ssl/private/ssl-cert-snakeoil.key /etc/ssl/private/dovecot.pem

Then I restarted Dovecot and it seemed to  work.  Now I just need to figure out how to get fetchmail to stop complaining about the "self-signed key".

-a.d-

---

### Post by Clochard on 2008-03-29
Nice, thank you - and bookmarked for 5 years down the line ;)

Combined with the [Remember Mismatched Domains]("https://addons.mozilla.org/en-US/thunderbird/addon/2131") add-on, launching TB is finally a no-dialogue exercise!

---

