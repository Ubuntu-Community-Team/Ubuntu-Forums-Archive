---
title: "Error on APT-GET"
date: 2007-02-13
forum: General Help
---

### Post by sdil on 2007-02-13
Do you know why my computer can't use apt-get easily ? It say : E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Can you say what is the problem and how to solve it. Please :(

---

### Post by Rhaddad on 2007-02-13
have you tried useing Sudo?

---

### Post by Kateikyoushi on 2007-02-13
I think this is not a permission issue that's error 13.
Are you sure you are not trying to use synaptic or aptitude same time ?

---

### Post by sdil on 2007-02-13
i have tried using synaptic and it say : Could not download all repo. indexes:confused:

---

### Post by sdil on 2007-02-13
can I know how to use Sudo ? Rhaddad

---

### Post by Nythain on 2007-02-13
are you using both at the same time... that error means something else is using apt currently... close any synaptic/adepts that are open, and try again... if none are open try a sudo killall aptitude or sudo killall apt-get???

---

### Post by daou on 2007-02-13
when you use apt-get from command line, you need to call sudo first:

sudo apt-get install blaa blaa

On the other hand, if you are using apt somewhere else (ex. Synaptic), you need to close them first. To check whether apt is already running, try something like this

ps -e | grep apt

It will show if any other apt process is running

---

### Post by sdil on 2007-02-13
Thanks to all of you. It works. :popcorn:

---

