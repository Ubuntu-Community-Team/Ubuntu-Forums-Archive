---
title: "Installing firefox, Libreoffice and thunderbird software"
date: 2013-08-04
forum: General Help
---

### Post by wheelie207 on 2013-08-04
I know that ubuntu team does well, but I would rather install firefox, libreoffice and thunderbird from the web site that makes them and not the ubuntu ones.
I have tried to install mozilla firefox downloaded from mozilla and ubuntu didn't reconize it.
Has installing the mozilla versions changed on ubuntu or not, as I have tried the ways earlier before unity came out.

I don't want the ubuntu versions of firefox, thunderbird and libreoffice and would like to know if installing them have changed or not.

---

### Post by vasa1 on 2013-08-04
> **wheelie207 said:**
> I know that ubuntu team does well, but I would rather install firefox, libreoffice and thunderbird from the web site that makes them and not the ubuntu ones.
I have tried to install mozilla firefox downloaded from mozilla and ubuntu didn't reconize it.
Has installing the mozilla versions changed on ubuntu or not, as I have tried the ways earlier before unity came out.

I don't want the ubuntu versions of firefox, thunderbird and libreoffice and would like to know if installing them have changed or not.
I don't know about T'bird but installing Firefox from Mozilla rather than from the software center works just fine. What exact problems are you having? You need to mention your desktop environment: Unity, KDE, LXDE, XFCE? 

I'm using LibreOffice from libreoffice.org and that comes with clear installation instructions. Again, you need to be explicit about what you need help in.

To answer the question you asked, the way to install these programs hasn't changed recently.

---

### Post by Buntu Bunny on 2013-08-04
You don't say which Ubuntu distro you are using, but maybe this article would help - "[Download and Install Firefox Manually in Ubuntu 12.04]("http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/")"

---

### Post by wheelie207 on 2013-08-04
> **vasa1 said:**
> I don't know about T'bird but installing Firefox from Mozilla rather than from the software center works just fine. What exact problems are you having? You need to mention your desktop environment: Unity, KDE, LXDE, XFCE? 

I'm using LibreOffice from libreoffice.org and that comes with clear installation instructions. Again, you need to be explicit about what you need help in.

To answer the question you asked, the way to install these programs hasn't changed recently.

Sorry, I'm running Ubuntu 13.04 with Unity.
When I installed it before it tells me that firefox is not installed and it was.

---

### Post by wheelie207 on 2013-08-04
> **Buntu Bunny said:**
> You don't say which Ubuntu distro you are using, but maybe this article would help - "[Download and Install Firefox Manually in Ubuntu 12.04]("http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/")"

Thanks for the link.

---

### Post by wheelie207 on 2013-08-05
> **Buntu Bunny said:**
> You don't say which Ubuntu distro you are using, but maybe this article would help - "[Download and Install Firefox Manually in Ubuntu 12.04]("http://www.liberiangeek.net/2012/04/download-and-install-firefox-manually-in-ubuntu-12-04-precise-pangolin/")"

I went to the website you had given me and followed it to a tee. I still get an error telling me that there was no command when I typed firefox in the terminal.

My question is: is the file name firefox executable or do I need to make the run-mozilla.sh executable.
That is the only thing I can think that is happening.

---

### Post by fdrake on 2013-08-05
try this too
"sudo chmod +x /opt/firefox12/firefox"

if you don't have any luck post here a screen shot of all your commands, please

---

### Post by wheelie207 on 2013-08-08
> **fdrake said:**
> try this too
"sudo chmod +x /opt/firefox12/firefox"

if you don't have any luck post here a screen shot of all your commands, please

Well, I am not making any progress at all.

Here is a post of my commands:

  	 	 	 	   harold@harold-MS-7592:~$ tar xjf ~/Downloads/firefox-22.0.tar.bz2  
 harold@harold-MS-7592:~$ sudo mv firefox/ /opt/firefox22  
 [sudo] password for harold:  
 harold@harold-MS-7592:~$ sudo mv /usr/bin/firefox /usr/bin/firefox-old  
 harold@harold-MS-7592:~$ sudo ln -s /opt/firefox22/firefox /usr/bin/firefox  
 harold@harold-MS-7592:~$ firefox  
 bash: /usr/bin/firefox: No such file or directory  
 harold@harold-MS-7592:~$  
 

 harold@harold-MS-7592:~$ sudo chmod +x /opt/firefox22/firefox 
 [sudo] password for harold:  
 harold@harold-MS-7592:~$ firefox 
 bash: /usr/bin/firefox: No such file or directory 

 harold@harold-MS-7592:~$  


As you can see, I tried the firefox command first and then I entered the chmod command and still nothing.

I did noticed that there is a file name called run-mozilla.sh ... I'm wondering why that file is not used to install firefox. I'm sure the script of that file could be change to install where it is need or maybe not.

I'm just trying to get firefox installed on my box.

---

### Post by vasa1 on 2013-08-08
> **wheelie207 said:**
> Sorry, I'm running Ubuntu 13.04 with Unity.
When I installed it before it tells me that firefox is not installed and it was.
There's a lot I don't understand here. If you have done a regular installation of Ubuntu 13.04, you should have Firefox (from the Ubuntu / Mozilla team) installed by default. Did you get rid of it or not? If you did get rid of it, how did you do so?

Do you have a ~/.mozilla folder (even though you can't run Firefox)?

What functional browsers do you have currently?

---

### Post by vasa1 on 2013-08-08
BTW, OP sees:
```
harold@harold-MS-7592:~$ firefox
bash: /usr/bin/firefox: No such file or directory
harold@harold-MS-7592:~$ 
```
Is that a normal response?

---

### Post by wheelie207 on 2013-08-08
> **vasa1 said:**
> There's a lot I don't understand here. If you have done a regular installation of Ubuntu 13.04, you should have Firefox (from the Ubuntu / Mozilla team) installed by default. Did you get rid of it or not? If you did get rid of it, how did you do so?

Do you have a ~/.mozilla folder (even though you can't run Firefox)?

What functional browsers do you have currently?

I know firefox is on ubuntu by default, but I do not like how they modify firefox for ubuntu when they don't include everything that firefox has when released from mozilla. Also ubuntu-firefox won't let me install an add-on for it when it tells me I need firefox for the addon and it is firefox I was using. These are some of the reasons I want to install mozilla firefox from mozilla and not ubuntu's firefox.

The next thing is I am using the ubuntu-firefox right now, but if I want it off the linux box all you have to do is use the package manager to remove it and it will remove it for you.

I'm not sure about the ~/.mozilla file as I didn't think to look, but there should be a folder as such with the ubuntu-firefox..

I just remembered another way to install firefox, but it would install as local which I'll try when done writing this.

---

### Post by wheelie207 on 2013-08-08
> **vasa1 said:**
> BTW, OP sees:
```
harold@harold-MS-7592:~$ firefox
bash: /usr/bin/firefox: No such file or directory
harold@harold-MS-7592:~$ 
```
Is that a normal response?

I have never seen an error response like that before.
I have been reading some command files about that type of response and what to do about it if possible.

---

### Post by psychomieze on 2013-08-08
> **wheelie207 said:**
> 
Here is a post of my commands:

 harold@harold-MS-7592:~$ sudo mv firefox/ /opt/firefox22  
 [sudo] password for harold:  
 harold@harold-MS-7592:~$ sudo mv /usr/bin/firefox /usr/bin/firefox-old  
 harold@harold-MS-7592:~$ sudo ln -s /opt/firefox22/firefox /usr/bin/firefox  
 harold@harold-MS-7592:~$ firefox  
 bash: /usr/bin/firefox: No such file or directory  
 harold@harold-MS-7592:~$  


Are you sure the symlink is correct? /opt/firefox22/firefox does exist? And you can start firefox from that location?

---

### Post by vasa1 on 2013-08-08
> **wheelie207 said:**
> I know firefox is on ubuntu by default, but I do not like how they modify firefox for ubuntu when they don't include everything that firefox has when released from mozilla. Also ubuntu-firefox won't let me install an add-on for it when it tells me I need firefox for the addon and it is firefox I was using. ....
Can you provide exact details of what you think is not included? And which is the add-on in question that you can't install?

---

### Post by wheelie207 on 2013-08-10
> **vasa1 said:**
> Can you provide exact details of what you think is not included? And which is the add-on in question that you can't install?

I don't remember the addon now, but I was using ubuntu-firefox and looking for an addon and went to install it and it told me that firefox was needed for the addon.

---

### Post by wheelie207 on 2013-08-10
> **psychomieze said:**
> Are you sure the symlink is correct? /opt/firefox22/firefox does exist? And you can start firefox from that location?

The symlink is correct, but it just could not see the link or the system wasn't able to see it.

---

### Post by monkeybrain20122 on 2013-08-10
Firefox doesn't need installation. Just untar the tarball, open the folder click firefox-bin and it will start. You can put the folder in your home.

BTW, I don't think there is any difference between Ubuntu's firefox and firefox except for Ubuntu-integration. You can disable it from tools > addons > extensions. Since you cannot remember the addon, maybe it is only for WIndows?

---

### Post by fdrake on 2013-08-10
what is the output of 
"ls -al /usr/bin/firefox"
? 

also are you using the gnome terminal or a different/costumized terminal?
try this also :
"gnome-terminal -e firefox"

---

### Post by wheelie207 on 2013-08-15
> **fdrake said:**
> what is the output of 
"ls -al /usr/bin/firefox"
? 

also are you using the gnome terminal or a different/costumized terminal?
try this also :
"gnome-terminal -e firefox"

I'm using gnome-terminal

---

