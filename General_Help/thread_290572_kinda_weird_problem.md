---
title: "kinda weird problem"
date: 2006-11-01
forum: General Help
---

### Post by quad machine on 2006-11-01
i'm not sure to ask about this here but...
here's the problem:
i come from Croatia and i have many folders which contain in their names one of croatian letters: &#269;&#263;žš&#273;
those folders work ok under winxp but ubuntu can't see them
how can i make those folders visible?
btw renaming isn't an option...
thx for any help, greetings

---

### Post by metalsam on 2006-11-01
is their a czech language pack for ubuntu ? try installing that if there is one

---

### Post by bettlebrox on 2006-11-01
Maybe you don't have the needed fonts installed. Try the following command and see if any of the fonts/packages that get listed meet your needs:

apt-cache search croatia

---

### Post by quad machine on 2006-11-02
solved, i added utf8,umask=022 to the /etc/fstab and works ok now
thx for help

---

