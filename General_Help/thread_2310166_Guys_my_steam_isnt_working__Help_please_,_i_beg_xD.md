---
title: "Guys my steam isnt working ? Help please , i beg xD"
date: 2016-01-16
forum: General Help
---

### Post by hugopalianhp on 2016-01-16
Hey guys , recently i got my new pc and thought that id rather get ubuntu instead of windows , i knew its much more complicated to install stuff but ffs this is getting ridiculous .Im trying to install steam but everything i do doesnt work , i installed it from the website and i have it and i can see it, like when i search for steam and when i press on it nothing happens , i uninstalled it again and installed it  but nothing happens . :neutral: . I really dont want to have to change to windows but if no one will help me out here i think i might have to because im not a coder or anything , so please , anything i can do ? I also tryd to install it from the Ubuntu Software Centre but when i press on steam it says its not found or something , please help <3

just got the steam launcher , now it says "Couldn't set up Steam data - please contact technical support"

---

### Post by MikeCyber on 2016-01-17
Google is your friend. You have installed multiple times to differen locations?
[http://askubuntu.com/questions/470436/steam-cannot-set-up-steam-data](http://askubuntu.com/questions/470436/steam-cannot-set-up-steam-data)

simply delete ~/.steam
(~ is your home )

never use root unless you absolutely need to

---

### Post by hugopalianhp on 2016-01-17
i did and nothing happened :(
mv ~/.steam/steam/* ~/.local/share/Steam/
rmdir ~/.steam/steam
ln -s ../.local/share/Steam ~/.steam/steam
rm -rf ~/.steam/bin

---

### Post by Sableyes on 2016-01-17
Of the 4 commands you posted none seem to just remove the steam folder.

Try uninstalling steam, then run the following commands then re install Steam :

cd ~
rm -rf .steam

---

### Post by hugopalianhp on 2016-01-18
i know i probably sound stupid but how do i uninstall it ? i go on and press uninstall nothing happens .

---

### Post by Sableyes on 2016-01-18
Open terminal and enter - 

sudo apt-get purge steam

---

### Post by maxinstuff2 on 2016-01-18
If you are new to ubuntu, I cannot recommend synaptic package manager to you enough.

in a terminal, type in:
```
sudo apt-get install synaptic
```

Then you can use the synaptic GUI to install anything from the repos (including steam).
It will also help you completely remove steam as suggested above.

---

### Post by hugopalianhp on 2016-01-22
Guys did some stuff with steam and this came up , it looks like its trying to update and it keeps failing , anything i can do ?

---

### Post by Petro Dawg on 2016-01-23
Removing comment/question.  Apparently you had multiple threads with my question already addressed by others.

---

### Post by lisati on 2016-01-23
Threads merged.

---

