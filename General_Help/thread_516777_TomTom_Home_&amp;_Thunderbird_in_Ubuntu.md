---
title: "TomTom Home &amp; Thunderbird in Ubuntu"
date: 2007-08-03
forum: General Help
---

### Post by baz.g on 2007-08-03
Hi, I am completely new to Linux and have made the switch this morning, I have managed to successfully install most of the programs i need but have found 2 stumbling blocks:

TomTom Home, I have searched through these forums and on google about this and cannot find any mention about the problem i am having, only about update problems after installation. Well, i cant install it at all :( I have already installed Wine and then i downloaded the latest tomtom home install .exe from tomtom.com, when i run it with wine i get the first couple of installation screens but then when i get to the screen that says "The Installshield Wizard will install TomTom Home 1.5.106 on your computer. To continue, click next" when i click next, the installer just hangs :(

I have another issue with Thunderbird, i followed some instructions on here about installing thunderbird 2.0.0.0 and it runs fine, but i cannot select it properly as a preferred application and it also doesnt show up in the add/remove menu so i cannot install it even if i wanted to.

Someone please help a ubuntu newbie! :) :) :)

Many Thanks

Baz

---

### Post by sdowney717 on 2007-08-03
you could always install virtualbox from virtualbox.org

And setup a virtual machine of windows XP that runs inside of linux. It is really interesting to see it boot up. It runs off a single virtual file and you can take a snapshot of the virtual machine and restore it.

This way you wont have to dual boot and can just start up a virtual XP like any other program inside of ubuntu.
[http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices](http://doc.gwos.org/index.php/VirtualBox#Enable_USB_devices)

virtualbox.org has a .deb for downloading the program

and also install the virtualbox additions for effortless mouse integration, USB and networking.

---

### Post by phidia on 2007-08-03
I don't know anything about tomtom, but since you're trying to run it through wine it must be a windows app. You may want to take a look at crossover office that sometimes works when wine doesn't-that's just my opinion.

About thunderbird, you didn't say exactly how you installed it or what version of ubuntu you're using. As a new user the best way to install software is from the System menu Administration, Synaptic Package Manager. If you use the package manager to install software you should be able to find the successfully install software in Applications.
Also note that thunderbird will be found listed as mozilla-thunderbird.

---

### Post by baz.g on 2007-08-04
sorry, i am running ubuntu 7.04, i downloaded thunderbird-2.0.0.6.tar.gz and installed it by:

sudo tar -C /opt -zxvf ~/Desktop/thunderbird-2.0.0.6#

deb [http://ubuntu.iculano.it](http://ubuntu.iculano.it) feisty thunderbird

i was just following the instructions posted on the [http://ubuntu.iculan.it](http://ubuntu.iculan.it) website and although thunderbird 2.0 is installed and works and shows up in the applications menu, it does not show up in the add/remove programs menu so i am unable to install it that way.

how else can i uninstall it please? since then i have installed thunderbird 1.5.10 from the add/remove programs menu and wish to continue using that instead.

many thanks in advance,

Baz :)

---

### Post by baz.g on 2007-08-05
ok, i installed virtual box and set up a virtual machine but when i click start i get:

```

The VirtualBox kernel driver is not accessible to the current user. Make sure that the user has write permissions for /dev/vboxdrv by adding them to the vboxusers groups. You will need to logout for the change to take effect..
VBox status code: -1909 (VERR_VM_DRIVER_NOT_ACCESSIBLE).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

```

and when i try to add the user i get:

```

administrator@administrator-laptop:~$ usermod -G vboxusers -a administrator
usermod: unable to lock password file

```

:( i thought i was getting somewhere too :(

lol oh well everybody has to start somewhere ey? :)

pleeeez help again :)

---

### Post by Andronicus on 2007-08-11
> **baz.g said:**
> sorry, i am running ubuntu 7.04, i downloaded thunderbird-2.0.0.6.tar.gz and installed it by:

sudo tar -C /opt -zxvf ~/Desktop/thunderbird-2.0.0.6#

deb [http://ubuntu.iculano.it](http://ubuntu.iculano.it) feisty thunderbird

i was just following the instructions posted on the [http://ubuntu.iculan.it](http://ubuntu.iculan.it) website and although thunderbird 2.0 is installed and works and shows up in the applications menu, it does not show up in the add/remove programs menu so i am unable to install it that way.

how else can i uninstall it please? since then i have installed thunderbird 1.5.10 from the add/remove programs menu and wish to continue using that instead.

many thanks in advance,

Baz :)

Extract the package in Nautilus; rightclick, extract here…..
Move the extracted folder to /usr/local/ :
Open your terminal and do :

    sudo mv /path/to/thunderbird /usr/local/
'
To make thunderbird executable with the command “thunderbird” do (one line):

    sudo ln -s /usr/local/thunderbird/thunderbird /usr/local/bin/thunderbird

If you wish to add the new thunderbird to your menu open alacarte with the command “alacarte”:
Select internet , then new item, name it Thunderbird or Thunderbird2.0 if you wish to run it next to the official ubuntu package.
Command is thunderbird.
Click the no icon button and select the thunderbird icon from here: /usr/local/thunderbird/icons
Click ok and make your selection.

Not happy with the new thunderbird ?

    sudo rm -rf /usr/local/thunderbird/
    sudo rm /usr/local/bin/thunderbird

Remove it from your menu with alacarte.

Ciao

---

### Post by nanotube on 2007-08-23
ubuntuzilla automates the install of the latest mozilla software, including thunderbird.
see the ubuntuzilla project link in my sig.

---

### Post by KhanTG on 2008-01-15
> **baz.g said:**
> Hi, I am completely new to Linux and have made the switch this morning, I have managed to successfully install most of the programs i need but have found 2 stumbling blocks:

TomTom Home, I have searched through these forums and on google about this and cannot find any mention about the problem i am having, only about update problems after installation. Well, i cant install it at all :( I have already installed Wine and then i downloaded the latest tomtom home install .exe from tomtom.com, when i run it with wine i get the first couple of installation screens but then when i get to the screen that says "The Installshield Wizard will install TomTom Home 1.5.106 on your computer. To continue, click next" when i click next, the installer just hangs :(

I have another issue with Thunderbird, i followed some instructions on here about installing thunderbird 2.0.0.0 and it runs fine, but i cannot select it properly as a preferred application and it also doesnt show up in the add/remove menu so i cannot install it even if i wanted to.

Someone please help a ubuntu newbie! :) :) :)

Many Thanks

Baz

I believe that this may solve the issue for the tomtom: [http://linux.softpedia.com/get/Science-and-Engineering/Geographical/TomTom-Go-16769.shtml](http://linux.softpedia.com/get/Science-and-Engineering/Geographical/TomTom-Go-16769.shtml)
I am trying it out and will post my results back here.

---

### Post by shanepardue on 2008-06-12
I really wish I could use TomTom Home in Linux..That's the only reason I have a Virtualbox machine.

---

### Post by Frank007 on 2008-06-26
I am using Ubuntu 7.04, Wine 0.9.46.
The TomTom Home program v1.1 worked fine for me.
Make sure that you have 'msvcr80(native,builtin)' in the 'libraries' section of your wine configuration.
One oddity is that the opening splash screen (which you can select not to appear), appears frozen until you hit 'esc'. Otherwise all functions work. You may want to seek out one of these older Home versions if later ones give you trouble.

Frank

---

### Post by shanepardue on 2008-06-26
> **Frank007 said:**
> I am using Ubuntu 7.04, Wine 0.9.46.
The TomTom Home program v1.1 worked fine for me.
Make sure that you have 'msvcr80(native,builtin)' in the 'libraries' section of your wine configuration.
One oddity is that the opening splash screen (which you can select not to appear), appears frozen until you hit 'esc'. Otherwise all functions work. You may want to seek out one of these older Home versions if later ones give you trouble.

Frank
Did it recognize your TomTom device also? I was able to get it running, but it never recognized my One XL.

---

