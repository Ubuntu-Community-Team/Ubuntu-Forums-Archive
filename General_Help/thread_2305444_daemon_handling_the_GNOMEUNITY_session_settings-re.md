---
title: "daemon handling the GNOME/UNITY session settings-requires installation of untrusted"
date: 2015-12-06
forum: General Help
---

### Post by drorlev on 2015-12-06
Hello.

I'm running Ubuntu 14.04 and for quite some time the software-updater suggests to update these packages:
[LIST]
daemon handling the GNOME session settings
[*]daemon handling the Unity session settings
[*]Gnome-settings-daemon schemas
[/LIST]
only to return with this message: "requires installation of untrusted packages"

I'll appreciate an explanation and suggestions how to get rid of this.

Thanks!
dror

---

### Post by Ricardo_Velasco on 2015-12-06
Greeting:

In the terminal run:

>  sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade 

---

### Post by Vladlenin5000 on 2015-12-06
> **Ricardo_Velasco said:**
> Greeting:

In the terminal run:

+1

And please post any error message you get.

---

### Post by Ricardo_Velasco on 2015-12-06
Well, that was a possible solution but a little more research and found that other possible solution:

> sudo apt-get clean

sudo mv /var/lib/apt/lists /var/lib/apt/lists.bak

sudo mkdir -p /var/lib/apt/lists/partial

sudo apt-get clean
 
sudo apt-get update



---

### Post by drorlev on 2015-12-09
> **Vladlenin5000 said:**
> +1

And please post any error message you get.

Thanks for the replies. 

I tried running in the terminal all three commands (update, upgrade, dist-upgrade). 

For both upgrade and dist-upgrade I get this message:
> WARNING: The following packages cannot be authenticated!
  gnome-settings-daemon gnome-settings-daemon-schemas unity-settings-daemon


Any idea why these packages cannot be authenticated? Isn't it worrying that seemingly base packages aren't authenticated? 

Would the other (more complicated in my view) way - with the 'clean' command, resolve this?

Thanks!
dror

---

### Post by Ricardo_Velasco on 2015-12-09
Greetings:

Try running these commands :


> sudo apt-key update

sudo apt-get update



---

### Post by Vladlenin5000 on 2015-12-09
> **drorlev said:**
> Any idea why these packages cannot be authenticated? Isn't it worrying that seemingly base packages aren't authenticated? 

One explanation would be some PPA for Gnome you might have add. If you haven't then the previous commands should have some effect. Post back if your symptom persists.

---

### Post by CantankRus on 2015-12-09
Might be helpful to show enabled ppa's.
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

---

### Post by drorlev on 2015-12-10
> **CantankRus said:**
> Might be helpful to show enabled ppa's.
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```

Well, the update-upgrade didn't work and I did have installed some ppa on this machine, so I used CantankRus's suggestion to list my ppa's, found a suspicious ppa, unchecked it from the software-source list and the trouble is over! :)

Thanks for the help!!

dror

---

