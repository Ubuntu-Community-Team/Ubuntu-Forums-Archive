---
title: "how to check if a font is installed or not ?"
date: 2012-11-14
forum: General Help
---

### Post by winzip on 2012-11-14
I  have a font-installation manual as this ...



[LIST]
[*]                   *As root/superuser, run:*
                   [I]apt-get install ttf-sinhala-lklug ibus im-switch ibus-m17n m17n-db m17n-contrib 
language-pack-si-base[/I]
[/LIST]
               
[LIST]
[*]                   *From your user account (i.e. not root) run:*
                   *rm -f ~/.xinput.d/* ; im-switch -z all_ALL -s ibus*
[/LIST]
               
[LIST]
[*]                   *Logout and login again. Environment variables need to be set/updated (NO NEED TO REBOOT)*
[/LIST]
                                  *From your user account (i.e. not root) select your keyboard layouts by running:*
                   *ibus-setup*




[B]How do I check if this font has already been installed or not in the system ?   Is there any command to check ?  

OS: Ubuntu 10 Server Edition
[/B]

---

### Post by carl4926 on 2012-11-14
Check in
/usr/share/fonts

---

### Post by winzip on 2012-11-14
> **carl4926 said:**
> Check in
/usr/share/fonts

There would be many font listing ...is not it ? How do I check if this particular font has been installed or not ? what to search  ?

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> There would be many font listing ...is not it ? How do I check if this particular font has been installed or not ? what to search  ?
most probably font name will be [S]sinhala.ttf[/S] lklug.ttf or something like that. Alternately you can open any text editor like gedit and the installed font shall be present in that list.

---

### Post by NikTh on 2012-11-14
Hi ,

I guess the font is [COLOR=Blue][COLOR=Black]this => [/COLOR][/COLOR][I][COLOR=Blue][B][COLOR=Black]ttf-sinhala-lklug
[/COLOR][/B][/COLOR][/I][COLOR=Blue][COLOR=Black]you can see if installed with 
```
dpkg -l | grep -i sinhala
```or search in /usr/share/fonts like this
```
rgrep -i sinhala /usr/share/fonts/
```

Thanks
[/COLOR][/COLOR]

---

### Post by raja.genupula on 2012-11-14
Actually there is command to list all the fonts installed . that is **fc-list**
[http://manpages.ubuntu.com/manpages/hardy/man1/fc-list.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/fc-list.1.html)

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> Alternately you can open any text editor like gedit and the installed font shall be present in that list.

its UBUNTU 10 SERVER EDITION ....no GUI supported.

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> its UBUNTU 10 SERVER EDITION ....no GUI supported.


Then you got cat command which display the content of a file .

```
cat <filename>
```

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> its UBUNTU 10 SERVER EDITION ....no GUI supported.
In that case you can do 
```
fc-list | grep -i lklug
```

---

### Post by NikTh on 2012-11-14
> **raja.genupula said:**
> Actually there is command to list all the fonts installed . that is **fc-list**

Didn't know that . 
Learning every day :) 
Thanks

---

### Post by Elfy on 2012-11-14
> _**Use color and font properties for highlighting portions of your tex**_t, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] non-uniform font size/color is difficult for those who are visually impaired. If you are having problems with reading the font, please adjust your browser.

Color removed.

---

### Post by raja.genupula on 2012-11-14
> **NikTh said:**
> Didn't know that . 
Learning every day :) 
Thanks

Welcome My friend .

---

### Post by winzip on 2012-11-14
> **raja.genupula said:**
> [COLOR=Red]Actually there is command to list all the fonts installed . that is **fc-list**[/COLOR]
[http://manpages.ubuntu.com/manpages/hardy/man1/fc-list.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/fc-list.1.html)

I  get this ....

**$ fc -list**
[I]-bash: fc: -i: invalid option
fc: usage: fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command][/I]

---

### Post by winzip on 2012-11-14
> **NikTh said:**
> Hi ,
[COLOR=Blue][COLOR=Black]***```
rgrep -i sinhala /usr/share/fonts/
```***Thanks
[/COLOR][/COLOR]

I get this ...

**$ rgrep -i sinhala /usr/share/fonts/**
*grep: /usr/share/fonts/: No such file or directory*

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> I  get this ....

**$ fc -list**
[I]-bash: fc: -i: invalid option
fc: usage: fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command][/I]


See there is no space between fc & -list

actual command 
```
fc-list 
```

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> I  get this ....

**$ fc -list**
[I]-bash: fc: -i: invalid option
fc: usage: fc [-e ename] [-lnr] [first] [last] or fc -s [pat=rep] [command][/I]
-list is not an aurgument to fc command here. fc-list is itself a cammand. and this fc-list will list all installed fonts which might become quite difficult to read so use grep to find the most probable font name as I mentioned in my last post. That command shall spit out all possible entries with "lklug" which in your case is the font name "lklug.ttf" which is a sinhala language font.

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> I get this ...

**$ rgrep -i sinhala /usr/share/fonts/**
*grep: /usr/share/fonts/: No such file or directory*


actually you have  to read something 
here you go

> There are various locations in GNU/Linux in which fonts can be kept. These locations are defined in /etc/fonts/fonts.conf; standard ones include /usr/share/fonts, /usr/local/share/fonts, and /home/<username>/.fonts (where <username> is your user name). 
The  easiest way to install a truetype font is to press alt-F2 and enter the  following code (this will open nautilus in the right directory): 

gksu nautilus /usr/share/fonts/truetypeThen  create a new directory, name the directory whatever you like (choose a  name that you remember if you ever need to backup your fonts personal  fonts). Copy the fonts into that directory and finally rebuild the font  information files by pressing alt-F2, mark 'run in terminal' so you can  see the progress and entering the following code: 

sudo fc-cache -f -v

source:[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by winzip on 2012-11-14
> **raja.genupula said:**
> See there is no space between fc & -list

actual command 
```
fc-list 
```

I get this ...

**$ fc-list**
[I]The program 'fc-list' is currently not installed.  To run 'fc-list' please ask your administrator to install the package 'fontconfig'

[/I]I'm not administrator.  Is there any other way I can check whether font  ** ttf-sinhala-lklug **is installed or not ?

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> I get this ...

**$ fc-list**
[I]The program 'fc-list' is currently not installed.  To run 'fc-list' please ask your administrator to install the package 'fontconfig'

[/I]I'm not administrator.  Is there any other way I can check whether font  ** ttf-sinhala-lklug **is installed or not ?

in the post No. #17 , there are all possible locations to have fonts and they all wort a try.

---

### Post by winzip on 2012-11-14
> **raja.genupula said:**
> actually you have  to read something 
here you go



source:[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Is there any command which could search all these required font-paths to check if  ***ttf-sinhala-lklug *** has been installed or not ?
I may not be sure how many such font-paths would be in the system.

---

### Post by NikTh on 2012-11-14
> **winzip said:**
> I get this ...

I'm not administrator.  Is there any other way I can check whether font  ** ttf-sinhala-lklug **is installed or not ?

If you are not administrator (you have not root privileges) then you cannot install anything. So I assume the installation you described in first post not permitted. 

Alternatively you can try to search in various folders (see @raja.genupula's post above) or use the locate command 

```
locate sinhala
```
or
```
locate lklug
```

---

### Post by raja.genupula on 2012-11-14
> **NikTh said:**
> If you are not administrator (you have not root privileges) then you cannot install anything. So I assume the installation you described in first post not permitted. 

Alternatively you can try to search in various folders (see @raja.genupula's post above) or use the locate command 

```
locate sinhala
```or
```
locate lklug
```


Yeah +1 .

---

### Post by winzip on 2012-11-14
> **NikTh said:**
>  So I assume the installation you described in first post not permitted. 


I'm not installing . I a checking whether administrator has installed or forgot to install. I looked up the manual to find the font-name.  Now I am trying to find whether it has been installed or not .

> 
Alternatively you can try to search in various folders (see @raja.genupula's post above) or use the locate command 

```
locate sinhala
```or
```
locate lklug
```

Will try  this  and  post result here ........is not  **locate  *****ttf*-*sinhala*-*****lklug**   *should be better here ?

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> I'm not installing . I a checking whether administrator has installed or forgot to install. I looked up the manual to find the font-name.  Now I am trying to find whether it has been installed or not .



Will try  this  and  post result here ........is not  **locate  *****ttf*-*sinhala*-*****lklug**   *should be better here ?
if the install was done recently and the .deb package is still in the apt cache then using
locate  *ttf*-*sinhala*-*lklug*
might also work. to confirm this you can look in /var/cache/apt/archives folder were all the downloaded .debs are kept till cache cleaning.

---

### Post by winzip on 2012-11-14
> **winzip said:**
> I'm not installing . I a checking whether administrator has installed or forgot to install. I looked up the manual to find the font-name.  Now I am trying to find whether it has been installed or not .



Will try  this  and  post result here ........is not  **locate  *****ttf*-*sinhala*-*****lklug**   *should be better here ?

I get this ...

**$locate sinhala**
/usr/share/vim/vim72/keymap/sinhala-phonetic_utf-8.vim
/usr/share/vim/vim72/keymap/sinhala.vim

**$locate lklug**  ------------> returns nothing

**$locate  *****ttf*-*sinhala*-*****lklug*** -----------> returns nothing


Does this mean sinhala  fonts are installed ?

---

### Post by raja.genupula on 2012-11-14
> **$locate sinhala**
/usr/share/vim/vim72/keymap/sinhala-phonetic_utf-8.vim
/usr/share/vim/vim72/keymap/sinhala.vim

That means they got for VIM and not for total system .

---

### Post by raja.genupula on 2012-11-14
ask your administrator to get them installed and fc-list for future need .

---

### Post by winzip on 2012-11-14
> **raja.genupula said:**
> That means they got for VIM and [COLOR=Red]**not for total system **[/COLOR].


What  it  would have returned  if it were  for total system ?

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> What  it  would have returned  if it were  for total system ?
it should return from the any location that i have mentioned in the post # 17.

---

### Post by winzip on 2012-11-14
Thanks.

I  have got a sudo access now ....  I'll  try installing  now....can you please tell how to install   fcconfig  first  so that I can  use  fc-list  in future need ?

Also does   fcconfig  installation requires a reboot ?  I am using putty

I'll keep on posting updates here.

---

### Post by winzip on 2012-11-14
<I'm closing this thread now >

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> Is this the correct command to install font config ?

**sudo apt-get install fontconfig**

Do I need a reboot ?
yes the format of command is correct.
I don't think a reboot shall be required.

---

### Post by winzip on 2012-11-14
Can you please tell whether fontconfig installation is successful ?

I don't see any success message here and hence I'm worried.
[B]

$sudo apt-get install fontconfig[/B]


Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openbravo-erp : Depends: openjdk-6-jdk but it is not going to be installed
                 Depends: postgresql but it is not going to be installed
                 Depends: postgresql-contrib but it is not going to be installed
                 Depends: postgresql-client
                 Depends: ant
                 Depends: ant-optional
                 Depends: libapache2-mod-jk but it is not going to be installed
                 Depends: libtcnative-1 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by pkadeel on 2012-11-14
No it was not installed and it recommends that you first check your system for unmet dependencies using 
```

apt-get -f install

```
I suggest though you better focus on installing the font and other things required which you mention in your other thread instead of going for the fontconfig package.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> No it was not installed and it recommends that you first check your system for unmet dependencies using 
```

apt-get -f install

```I suggest though you better focus on installing the font and other things required which you mention in your other thread instead of going for the fontconfig package.

Thanks...you are right.

when I do this apt-get -f install ...it says  "After this operation, 96.2MB of additional disk space will be used".

I aborted this....its not high priority.



Well, I'm going ahead with the font installation then...

manual says this ...

[LIST]
[*]               *As root/superuser, run:*
               *apt-get install [COLOR=SeaGreen]**ttf-sinhala-lklug**[/COLOR] [COLOR=Red]**ibus im-switch ibus-m17n m17n-db m17n-contrib**[/COLOR]*
[*]               *From your user account (i.e. not root) run:*
               *rm -f ~/.xinput.d/* ; im-switch -z all_ALL -s ibus*
[*]               *Logout and login again. Environment variables need to be set/updated (NO NEED TO REBOOT)*
[*]               *From your user account (i.e. not root) select your keyboard layouts by running:*
[*]*ibus-setup*
[/LIST]




Can you please tell what are  ***[COLOR=Red]ibus im-switch ibus-m17n m17n-db m17n-contrib ?[/COLOR] ***I  don't think these are fonts.  what are these ? 

shall I skip these and  run this instead ..
[I]
apt-get install [COLOR=SeaGreen]**ttf-sinhala-lklug**[/COLOR][/I]

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> Thanks...you are right.

when I do this apt-get -f install ...it says  "After this operation, 96.2MB of additional disk space will be used".

I aborted this....its not high priority.



Well, I'm going ahead with the font installation then...

manual says this ...

[LIST]
[*]               *As root/superuser, run:*
               *apt-get install [COLOR=SeaGreen]**ttf-sinhala-lklug**[/COLOR] [COLOR=Red]**ibus im-switch ibus-m17n m17n-db m17n-contrib**[/COLOR]*
[*]               *From your user account (i.e. not root) run:*
               *rm -f ~/.xinput.d/* ; im-switch -z all_ALL -s ibus*
[*]               *Logout and login again. Environment variables need to be set/updated (NO NEED TO REBOOT)*
[*]               *From your user account (i.e. not root) select your keyboard layouts by running:*
[*]*ibus-setup*
[/LIST]




Can you please tell what are  ***[COLOR=Red]ibus im-switch ibus-m17n m17n-db m17n-contrib ?[/COLOR] ***I  don't think these are fonts.  what are these ? 

shall I skip these and  run this instead ..
[I]
apt-get install [COLOR=SeaGreen]**ttf-sinhala-lklug**[/COLOR][/I]
As far as I know, these are input method switcher packages means keyboard layout switcher. Might be required if you want to type in sinhali. I am not sure about the studio version you are using but on a normal desktop version these a preinstalled yet I never had to use these to switch my keyboard layout for complex text languages.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> I am not sure about the studio version you are using 

I'm using Ubuntu 10 server edition.

I put a locate command to check if these are per-installed or not..  ...this is what I get 


$locate ibus
/lib/libusb-0.1.so.4
/lib/libusb-0.1.so.4.4.4
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-common.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mb.ko
/lib/modules/2.6.35-22-generic-pae/kernel/drivers/media/dvb/dvb-usb/dvb-usb-dibusb-mc.ko
/usr/lib/libusb-0.1.so.4
/usr/share/doc/libusb-0.1-4
/usr/share/doc/libusb-0.1-4/README.Debian
/usr/share/doc/libusb-0.1-4/changelog.Debian.gz
/usr/share/doc/libusb-0.1-4/changelog.gz
/usr/share/doc/libusb-0.1-4/copyright
/usr/src/linux-headers-2.6.35-22/arch/ia64/include/asm/sn/pcibus_provider_defs.h
/usr/src/linux-headers-2.6.35-22-generic-pae/include/config/dvb/usb/dibusb
/usr/src/linux-headers-2.6.35-22-generic-pae/include/config/dvb/usb/dibusb/mb.h
/usr/src/linux-headers-2.6.35-22-generic-pae/include/config/dvb/usb/dibusb/mc.h
/var/lib/dpkg/info/libusb-0.1-4.list
/var/lib/dpkg/info/libusb-0.1-4.md5sums
/var/lib/dpkg/info/libusb-0.1-4.postinst
/var/lib/dpkg/info/libusb-0.1-4.postrm
/var/lib/dpkg/info/libusb-0.1-4.shlibs


$locate im-switch
/usr/share/language-selector/data/im-switch.blacklist


$locate  ibus-m17n  ---->returns nothing

$locate m17n-db ---->returns nothing

$locate m17n-contrib  ---->returns nothing



Shall I just shoot  [I].....

[COLOR=Black]apt-get install [/COLOR][COLOR=SeaGreen][B][COLOR=Black]ttf-sinhala-lklug[/COLOR]

[COLOR=Black]or [/COLOR]

[/B][/COLOR][/I][COLOR=Black]*apt-get install **ttf-sinhala-lklug** **ibus im-switch ibus-m17n m17n-db m17n-contrib***[/COLOR][I][COLOR=SeaGreen][B][COLOR=Black]  [/COLOR]

?
[/B][/COLOR][/I]

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> I'm using Ubuntu 10 server edition.
That is what I ment. I am not sure about it because I have never used it.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> That is what I ment. I am not sure about it because I have never used it.

have updated my post with findings ...which command to shoot  ? what do you think ?

I may not require  keyboard stuff at this moment .....but rather interested to install the font.


(because my web application  hosted in this Box  is generating pdf files and characters becoming scrambled)

---

### Post by pkadeel on 2012-11-14
first only install the font
```
sudo apt-get install [COLOR=SeaGreen][COLOR=Black]ttf-sinhala-lklug[/COLOR][/COLOR]
```
Then check if your actual requirement is met or not. If your actaul requirement is not satisfied then you can always install the remaining packages.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> first only install the font
```
sudo apt-get install [COLOR=SeaGreen][COLOR=Black]ttf-sinhala-lklug[/COLOR][/COLOR]
```Then check if your actual requirement is met or not. If your actaul requirement is not satisfied then you can always install the remaining packages.

Ok thanks...

will  check installation and update here soon.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> first only install the font
```
sudo apt-get install [COLOR=SeaGreen][COLOR=Black]ttf-sinhala-lklug[/COLOR][/COLOR]
```Then check if your actual requirement is met or not. If your actaul requirement is not satisfied then you can always install the remaining packages.


font  not installed .....I get this ....

**$sudo apt-get install ttf-sinhala-lklug**

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openbravo-erp : Depends: openjdk-6-jdk but it is not going to be installed
                 Depends: postgresql but it is not going to be installed
                 Depends: postgresql-contrib but it is not going to be installed
                 Depends: postgresql-client
                 Depends: ant
                 Depends: ant-optional
                 Depends: libapache2-mod-jk but it is not going to be installed
                 Depends: libtcnative-1 but it is not going to be installed
 ttf-sinhala-lklug : Depends: defoma but it is not going to be installed
                     Recommends: x-ttcidfont-conf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by winzip on 2012-11-14
is not this font  exist in the system by default ?

or I need to download from the internet first ?

---

### Post by winzip on 2012-11-14
Here is the font download link tinyurl

**[http://tinyurl.com/czcympj](http://tinyurl.com/czcympj)**

Can you please check if you are able to install this font...

Please tell me the steps if you get any success.

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> font  not installed .....I get this ....

**$sudo apt-get install ttf-sinhala-lklug**

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openbravo-erp : Depends: openjdk-6-jdk but it is not going to be installed
                 Depends: postgresql but it is not going to be installed
                 Depends: postgresql-contrib but it is not going to be installed
                 Depends: postgresql-client
                 Depends: ant
                 Depends: ant-optional
                 Depends: libapache2-mod-jk but it is not going to be installed
                 Depends: libtcnative-1 but it is not going to be installed
 ttf-sinhala-lklug : Depends: defoma but it is not going to be installed
                     Recommends: x-ttcidfont-conf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
Well as you are not the admin of this machine and have borrowed sudo access to frank, let me suggest you a simple and easy method to achieve your goal.

All you need right now is to have a simple font file installed on your system. Correct me if I am wrong.

Now download the font from the web and put it in /usr/share/fonts/truetype/sinhala folder and rebuild font cache.

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> Well as you are not the admin of this machine and have borrowed sudo access to frank, let me suggest you a simple and easy method to achieve your goal.



I am testing  and simulating in a local system now  where I am logging into  the system with **root  **userid..

Here is what happens without  **sudo**    

**$apt-get install ttf-sinhala-lklug**

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 openbravo-erp : Depends: openjdk-6-jdk but it is not going to be installed
                 Depends: postgresql but it is not going to be installed
                 Depends: postgresql-contrib but it is not going to be installed
                 Depends: postgresql-client
                 Depends: ant
                 Depends: ant-optional
                 Depends: libapache2-mod-jk but it is not going to be installed
                 Depends: libtcnative-1 but it is not going to be installed
 ttf-sinhala-lklug : Depends: defoma but it is not going to be installed
                     Recommends: x-ttcidfont-conf but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> 
Now download the font from the web and put it in /usr/share/fonts/truetype/sinhala folder and rebuild font cache.

I have downloaded from the web.....Its a .tar.gz file.

I have a /usr/share/fonts/truetype/  folder.

I think you suggest me to make a sinhala folder here and put .tar.gz file here.

Don't I require to uncompress it ?  also how  a  admin rebuild font cache  ?

---

### Post by pkadeel on 2012-11-14
> **winzip said:**
> Here is the font download link tinyurl

**[http://tinyurl.com/czcympj](http://tinyurl.com/czcympj)**

Can you please check if you are able to install this font...

Please tell me the steps if you get any success.
The package present on this link contains a fonts folder besides other installable things.

Now I don't about the folder structure of your computer so you have to choose a location where you can download this package and replace "/path/where/you/can/download" with that path. replace "http://package_url with the complete file url"
first check whether sinhala and tamil folders are present in your fonts dir or not

```

cd /usr/share/fonts/truetype
ls -l

```if the folders are present then skip the next 2 mkdir commands otherwise do
```

sudo mkdir sinhala
sudo mkdir tamil

``````

cd /path/where/you/can/download
 wget -v http://tinyurl.com/czcympj -O icta_sinhala_tamil_installer_ubuntu_0.2.tar.gz
tar -zxf icta_sinhala_tamil_installer_ubuntu_0.2.tar.gz
cd icta_sinhala_tamil_installer_ubuntu/files/fonts/sinhala
sudo cp *.ttf /usr/share/fonts/truetype/sinhala/
cd ..
cd tamil
sudo cp *.ttf /usr/share/fonts/truetype/tamil/
sudo fc-cache -fv

```

---

### Post by raja.genupula on 2012-11-14
> **winzip said:**
> <I'm closing this thread now >


Hey

have you solved the issue ?

---

### Post by winzip on 2012-11-14
> **pkadeel said:**
> The package present on this link contains a fonts folder besides other installable things.

Now I don't about the folder structure of your computer so you have to choose a location where you can download this package and replace "/path/where/you/can/download" with that path. replace "http://package_url with the complete file url"
first check whether sinhala and tamil folders are present in your fonts dir or not

```

cd /usr/share/fonts/truetype
ls -l

```if the folders are present then skip the next 2 mkdir commands otherwise do
```

sudo mkdir sinhala
sudo mkdir tamil

``````

cd /path/where/you/can/download
 wget -v http://tinyurl.com/czcympj -O icta_sinhala_tamil_installer_ubuntu_0.2.tar.gz
tar -zxf icta_sinhala_tamil_installer_ubuntu_0.2.tar.gz
cd icta_sinhala_tamil_installer_ubuntu/files/fonts/sinhala
sudo cp *.ttf /usr/share/fonts/truetype/sinhala/
cd ..
cd tamil
sudo cp *.ttf /usr/share/fonts/truetype/tamil/
sudo fc-cache -fv

```

Thanks.....this is very much helpful.....I'll try  this....I'll update  here my findings ....please visit  this post again....I'll have a break for 2 hours  now....I'll post after 2 hours.

---

### Post by pkadeel on 2012-11-14
> **raja.genupula said:**
> Hey

have you solved the issue ?
nope he is on another thread now.
[http://ubuntuforums.org/showthread.php?t=2083986](http://ubuntuforums.org/showthread.php?t=2083986)

---

### Post by uRock on 2012-11-14
Duplicate threads merged.

---

### Post by winzip on 2012-11-15
font cache build not working

**# fc-cache -fv**
The program 'fc-cache' is currently not installed.  You can install it by typing:
apt-get install fontconfig

---

### Post by pkadeel on 2012-11-15
> **winzip said:**
> font cache build not working

**# fc-cache -fv**
The program 'fc-cache' is currently not installed.  You can install it by typing:
apt-get install fontconfig
After sending my last post I realized that you will again get stuck at cache update stage. Well I do not know about any other method to update font cache except this command. So you have only two options left I guess
Either get fontconfig package installed somehow
Or wait for someone else who knows how to rebuild font cache.

---

