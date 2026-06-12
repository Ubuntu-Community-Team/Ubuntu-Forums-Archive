---
title: "How do i import a  certificate into OpenOffice"
date: 2006-09-08
forum: General Help
---

### Post by dhruv_1884 on 2006-09-08
Hi guys,

I wanted to use the Digital Signature feature of OO but no certificates show up in the Add Certificate dialog box
I have a certificate from thwate for email signing in my mozilla-thunderbird profile
i checked the OOwiki site and they wanted an environmental variable to point to the profile folder, so i ran the command below in the terminal

```
export MOZILLA_CERTIFICATE_FOLDER=/home/dhruv/.mozilla-thunderbird/n6eet9wq.default

```

and yet no certificates show up in OO

any tips guys

thanks 

regards

dhruv

---

### Post by tuxinvader on 2006-09-08
The export only exports the variable to applications launched from that terminal. Did you launch OO from the same terminal after doing the export?

---

### Post by dhruv_1884 on 2006-09-08
no i didnt launc OO from the terminal.
i'll try to figure out how to launch OO from the terminal and try thatt export again

plz do send me a procedure for the same if possible


thanks

dhruv

---

### Post by dhruv_1884 on 2006-09-08
didnt work dude

this is what i did in the terminal

$ openoffice
$ export ........

and yet it didnt show up

---

### Post by dhruv_1884 on 2006-09-08
by the way site says Launch
export..........

---

### Post by dhruv_1884 on 2006-09-08
dude thanks it worked, when i did it the other way round
$ export.....
$ openoffice

---

### Post by tuxinvader on 2006-09-08
Cool. Yes you have to export before starting ;)

Now you've proved it works you should add the export to a file called .gnomerc in your home directory. Create it if it doesn't exist. Then you'll be able to launch it from the menu and not only the terminal.

 $ vi ~/.gnomerc

Cheers

---

### Post by VosaxAlo on 2006-10-14
Hi,

no way for me to make it function. 
At this site
[http://applications.linux.com/article.pl?sid=06/10/03/1859231&from=rss]("http://applications.linux.com/article.pl?sid=06/10/03/1859231&from=rss")

I have read that:
[COLOR="DarkRed"]On some Linux distros (notably, PCLinuxOS), OpenOffice.org only detects certificates which are installed in Mozilla Thunderbird (only if Thunderbird is installed on your machine). In this case, you need to export the certificate from Firefox and import it into Thunderbird.[/COLOR]

Perhaps Ubuntu is one of these Distros?
Or I make something wrong?

I use Ubuntu Dapper with OpenOffice 2.0.2

---

