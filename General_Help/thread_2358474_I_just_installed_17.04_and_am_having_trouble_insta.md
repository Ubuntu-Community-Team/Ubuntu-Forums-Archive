---
title: "I just installed 17.04 and am having trouble installing Chrome Browser"
date: 2017-04-13
forum: General Help
---

### Post by irv on 2017-04-13
I down loaded Chrome browser and tried to install using DEB package installer. Would not install so I tried a Terminal Install here here is what I am getting.
 ```
irv@irv-Q500A:~/Downloads$ ls
google-chrome-stable_current_amd64.deb
irv@irv-Q500A:~/Downloads$ sudo apt install google-chrome-stable_current_amd64.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package google-chrome-stable_current_amd64.deb
E: Couldn't find any package by glob 'google-chrome-stable_current_amd64.deb'
E: Couldn't find any package by regex 'google-chrome-stable_current_amd64.deb''
```
It's telling me it can't find the file but it's there. I did a copy paste so I wouldn't have any typeos

---

### Post by deadflowr on 2017-04-13
I think apt wants the full path, unlike dpkg which you can just move into the directory and install.
try with ~/Downloads/google-blah>.deb

---

### Post by irv on 2017-04-13
I followed the instructions on here and got it installed. I will mark it solved. 
[https://askubuntu.com/questions/510056/how-to-install-google-chrome]("https://askubuntu.com/questions/510056/how-to-install-google-chrome")

---

### Post by howefield on 2017-04-14
> **deadflowr said:**
> I think apt wants the full path, unlike dpkg which you can just move into the directory and install.
try with ~/Downloads/google-blah>.deb

+1 for apt needing the full path.

Sidenote : I generally copy/paste the file into the terminal and amend the path accordingly, tab completion doesn't work for me when doing a local deb package install with apt.

---

### Post by RobGoss on 2017-04-14
I believe Google chrome is also in the Ubuntu repository I just checked and I see it listed

---

### Post by coffeecat on 2017-04-14
> **RobGoss said:**
> I believe Google chrome is also in the Ubuntu repository I just checked and I see it listed

We need to distinguish the google-chrome-stable package from the chromium-browser package. The OP is referring to the google-chrome-stable package which is not in the Ubuntu repositories. You will only see google-chrome-stable in your package manager if you enable the [noparse]dl.google.com[/noparse] repository. This is enabled by installing the downloaded google-chrome-stable deb package. Chromium-browser, on the other hand, is in the Ubuntu Universe repository. 

For what it's worth, and for others coming across this thread, for google chrome I make sure I have gdebi installed (which I find more reliable than "Ubuntu Software" for downloaded deb packages), and then right-click on the google-chrome-stable deb file and "open with..." gdebi.

---

### Post by irv on 2017-04-14
> **coffeecat said:**
> We need to distinguish the google-chrome-stable package from the chromium-browser package. The OP is referring to the google-chrome-stable package which is not in the Ubuntu repositories. You will only see google-chrome-stable in your package manager if you enable the [noparse]dl.google.com[/noparse] repository. This is enabled by installing the downloaded google-chrome-stable deb package. Chromium-browser, on the other hand, is in the Ubuntu Universe repository. 

For what it's worth, and for others coming across this thread, for google chrome I make sure I have gdebi installed (which I find more reliable than "Ubuntu Software" for downloaded deb packages), and then right-click on the google-chrome-stable deb file and "open with..." gdebi.

Your right it is not in the repository. What I did was add it.
```
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
Then 
```
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google-chrome.list'
```
Did update
```
sudo apt update
```
Then installed the package.
```
sudo apt-get install google-chrome-stable
```

---

### Post by RobGoss on 2017-04-14
>       We need to distinguish the google-chrome-stable package from the chromium-browser package. The OP is referring to the google-chrome-stable package which is not in the Ubuntu repositories    

**Coffecat** you are correct about installing the gdebi installer I had to do this in one of my machines thanks for the clarification

---

