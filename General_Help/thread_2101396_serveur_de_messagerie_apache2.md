---
title: "serveur de messagerie apache2"
date: 2013-01-04
forum: General Help
---

### Post by yzahran on 2013-01-04
Bonjour tout le monde,
Je suis entrain de mise en place une solution messagerie sous ubuntu 12.04 LTS, Postfix, Dovecot, MySQL, j'ai suivi un tutoriel sous lien suivant [http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/) , mais j'ai rencontré un problème au niveau de la configuration:

**le première problème:**
lorsque je tape la commande 'sudo service apache2 restart' pour redémarrer le serveur apache2 j'ai le message d'erreur suivante:

Syntax error on line 51 of /etc/apache2/sitesenabled/default-ssl:
SSLCertificateFile: file '/path/to/my/cert.crt' does not exist or is empty
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!


**le deuxième problème:**
C'est que une fois j'ai tapé le setup password login administrateur et mot de passe de l'administrateur sur l'interface web postfxadmin et j’appuie sur add to domaine l’interface web postfixadmin est totalement détruite  et rien ne s'affiche sur l’écran .

s'il vous plaît j'aurai besoin de vos aides le plus vite possible


merci d'avance .

---

### Post by gnush on 2013-01-04
> Write your posts in English unless you are participating in a Loco  Forum, where you are permitted to use another language if it is in  common use in that Loco Forum and understood by the Loco Forum staff. We  have many users from many different countries that visit here and  English is the common language of these forums.*[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)*


Even though I don't understand what you're saying, I'm going to answer anyway.

Is it SELinux?

Check the logs and see if you can find anything of relevance there.

```
# cat /var/logs/messages
```Try to disable SELinux temporarily and see if you can run Apache.

---

