---
title: "limewire"
date: 2007-01-24
forum: General Help
---

### Post by naruto650 on 2007-01-24
I have download limewire for linux but ubuntu won't let me install it. How can i download it or install it so it works with Ubuntu?

---

### Post by Happy_Man on 2007-01-24
More information would be helpful. Is it .deb? .rpm? What errors come up (if any)?

---

### Post by jbayone on 2007-01-24
You may be better off installing Frostwire.  It's the linux equivalent to Limewire but without the ads.

---

### Post by naruto650 on 2007-01-24
its saids Couldn't display "/home/jonathan/Desktop/LimeWire/LimeWire.exe"

---

### Post by llamakc on 2007-01-24
Instead of trying to install the Windows binary on Linux, open Synaptic and install the package "frostwire."

---

### Post by naruto650 on 2007-01-24
> **jbayone said:**
> You may be better off installing Frostwire.  It's the linux equivalent to Limewire but without the ads.

Well i installed it and when i click on it to start it nothing happens.

---

### Post by Happy_Man on 2007-01-24
Well, you can't run Windows apps on Linux. You're gonna have to find an alternative. I would suggest installing Frostwire like the guys above said. It has everything LimeWire does, only it'll run on your system.:)

---

### Post by naruto650 on 2007-01-24
> **Happy_Man said:**
> Well, you can't run Windows apps on Linux. You're gonna have to find an alternative. I would suggest installing Frostwire like the guys above said. It has everything LimeWire does, only it'll run on your system.:)

Like i said before, i have installed it but nothing comes up. It won't
start.

---

### Post by llamakc on 2007-01-24
> **naruto650 said:**
> Well i installed it and when i click on it to start it nothing happens.

The Frostwire package hasn't been ported to Edgy's use of /bin/dash for sh. Do this:

> 
sudo dpkg-reconfigure dash
And choose NO.

Now frostwire should start for you.

---

### Post by naruto650 on 2007-01-24
> **llamakc said:**
> The Frostwire package hasn't been ported to Edgy's use of /bin/dash for sh. Do this:

And choose NO.

Now frostwire should start for you.

How do i do this?

---

### Post by llamakc on 2007-01-24
> **naruto650 said:**
> How do i do this?

Open a Terminal. Are you familiar with how to do this yet? Once you have it opened, cut/paste my command or retype it. You'll be prompted for your user password.

---

### Post by naruto650 on 2007-01-24
> **llamakc said:**
> Open a Terminal. Are you familiar with how to do this yet? Once you have it opened, cut/paste my command or retype it. You'll be prompted for your user password.

How do you open a terminal?

---

### Post by llamakc on 2007-01-24
If you are using Gnome, type on the keyboard: ALT-F2 (the alt key and the F2 key). This opens a dialog window. Type "gnome-terminal" inside of it.

Now you'll have a command prompt. Follow my above instructions about typing in this Terminal window:

sudo dpkg-reconfigure dash

...and choosing NO.

Start Frostwire and get your download on.

---

### Post by naruto650 on 2007-01-24
I did what you told me and this shows up. Package `dash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: dash is not installed

What now?

---

### Post by llamakc on 2007-01-24
Did you install Edgy, or are you on Dapper?

Do this while you have the Terminal open:

type:

> 
frostwire



It is going to either start or not. If it does NOT start, please cut and paste any of the output to the Terminal window HERE for us. Thanks.

---

### Post by naruto650 on 2007-01-24
> **llamakc said:**
> Did you install Edgy, or are you on Dapper?

Do this while you have the Terminal open:

type:



It is going to either start or not. If it does NOT start, please cut and paste any of the output to the Terminal window HERE for us. Thanks.

I did as you said and now this shows up, i don't know what kind i installed. I just know its called ubuntu.

 -desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by hscottyh on 2007-01-24
Your missing java, which Limewire or Frostwire depend on.

In the terminal type:
uname -r

and post back what you get, that will let us know what version of ubuntu you are on. From there we will tell you how to get java installed.

---

### Post by llamakc on 2007-01-24
Well you need to install JAVA.

You need to figure out WHAT you installed. 

IF you installed Edgy (you can check this by running the command in the Terminal


> 
cat /etc/lsb-release


and if it reads:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

Then use this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

and namely:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v5.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v5.0_with_Plug-in_for_Mozilla_Firefox)

You are going to HAVE to follow this directions carefully. That means reading up on how to add extra repositories, which I'm now assuming you have not done yet.

From here on out, please give more information on what you HAVE done yet. Let us know where you are with your knowledge of Linux/Ubuntu so we can help you help yourself the quickest way possible.

---

### Post by llamakc on 2007-01-24
By the way, there's probably easier ways to figure out if you're running Edgy in Gnome. I don't use Gnome/KDE so I'm unaware of how. I am comfortable with the command-line and my recommendations are going to be centered around that.

For starters, you've already learned how to type ALT-F2 and get Gnome-Terminal running. Once we get Frostwire running you would also be able to type ALT-F2 and enter frostwire in the window and get it running.

Good luck. Get JAVA installed and it should work just fine.

---

### Post by naruto650 on 2007-01-24
> **hscottyh said:**
> Your missing java, which Limewire or Frostwire depend on.

In the terminal type:
uname -r

and post back what you get, that will let us know what version of ubuntu you are on. From there we will tell you how to get java installed.

I entered that and it gave me this 2.6.15-27-386

---

### Post by naruto650 on 2007-01-24
> **llamakc said:**
> Well you need to install JAVA.

You need to figure out WHAT you installed. 

IF you installed Edgy (you can check this by running the command in the Terminal




and if it reads:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DESCRIPTION="Ubuntu 6.10"

Then use this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

and namely:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v5.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v5.0_with_Plug-in_for_Mozilla_Firefox)

You are going to HAVE to follow this directions carefully. That means reading up on how to add extra repositories, which I'm now assuming you have not done yet.

From here on out, please give more information on what you HAVE done yet. Let us know where you are with your knowledge of Linux/Ubuntu so we can help you help yourself the quickest way possible.


THis is what it gave me 

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"

---

### Post by llamakc on 2007-01-24
Okay, so you have Dapper installed.

You need to enable extra repositories in Synaptic for starters. Let's get that done and then we'll install JAVA.

---

### Post by hscottyh on 2007-01-24
To add the repository that contains sun's java do this.
Open synaptic:
System -> Administration -> Synaptic Package Manager

From the menu choose repositories, then check Multiverse.
It's somewhere in there. I'm on the newer version and the GUI changed a bit.
Then press the reload button in Synaptic.

Then to install java for Dapper (the version of ubuntu you have) follow the directions on this link:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by llamakc on 2007-01-24
> **llamakc said:**
> Okay, so you have Dapper installed.

You need to enable extra repositories in Synaptic for starters. Let's get that done and then we'll install JAVA.

> Ensure the relevant repositories are enabled. Click **System -> Administration -> Synaptic Package Manager -> Settings -> Repositories** and then click **Add**. Check the **Community maintained (Universe)**' and **Non-free (Multiverse) boxes.** When you close the window, click **Reload**.

[http://www.cs.cornell.edu/~djm/ubuntu/index_dapper.html#sun-java](http://www.cs.cornell.edu/~djm/ubuntu/index_dapper.html#sun-java)

Do that.

---

### Post by deadlydeathcone on 2007-01-24
I just wanted to point out that there are updated packages along with instructions [here]("http://www.frostwire.com/blog/?p=17").

---

### Post by naruto650 on 2007-01-24
> **hscottyh said:**
> To add the repository that contains sun's java do this.
Open synaptic:
System -> Administration -> Synaptic Package Manager

From the menu choose repositories, then check Multiverse.
It's somewhere in there. I'm on the newer version and the GUI changed a bit.
Then press the reload button in Synaptic.

Then to install java for Dapper (the version of ubuntu you have) follow the directions on this link:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

this is so hard. I did the refresh thing already and then i downloaded the j2se thing. but when i opened it, it said that Could not open the file /home/john/Desktop/jre-1_5_0_10-linux-i586.bin.

---

### Post by hscottyh on 2007-01-24
> **deadlydeathcone said:**
> I just wanted to point out that there are updated packages along with instructions [here]("http://www.frostwire.com/blog/?p=17").

I really like the Frostwire beta. Worth checking out, but get java installed first, and the version you have working, then dowload the beta if you want. It's very easy to install. Just download and click on the file. It will automatically start the installer.

---

### Post by llamakc on 2007-01-24
OP, please use Synaptic to INSTALL 

sun-java5-jre sun-java5-plugin

And then in the Terminal type:

sudo update-alternatives --config java

and select the sun java option.

You need to decide on whether or not to install JAVA via Ubuntu or manually. Our instructions are conflicting at this point. Either way will work, but you need to follow through with the instructions all of the way.

---

### Post by hscottyh on 2007-01-24
> **naruto650 said:**
> this is so hard. I did the refresh thing already and then i downloaded the j2se thing. but when i opened it, it said that Could not open the file /home/john/Desktop/jre-1_5_0_10-linux-i586.bin.

You don't need the bin file you downloaded. You get java from the repository we enabled.

Now that you got the extra repository enabled just past each of these two lines in the terminal one at a time:
sudo apt-get install sun-java5-jre sun-java5-plugin
sudo update-alternatives --config java

And Select the sun java option. You should be ready to rock then.

Don't get discouraged, it gets much easier once you understand a few things.
Oh, by the way the terminal is in the menu Applications -> Accessories -> Terminal

---

### Post by ashmew2 on 2007-01-24
I think u shud get Limewire off [www.Limewire.com](www.Limewire.com) or Limewire Pro of somewhere(AM i allowed to tell this here? ). I have a Limewire Pro setup.rpm which works fine on Edgy as well as Dapper Drake . ill tell u everything step by step if u havent yet figured out :D
By the way , Frostwire may be the blue clone of Limewire but i prefer LImewire :P Just my thoughts:D

---

### Post by hscottyh on 2007-01-24
I'm sorry the link I gave you on installing java had two ways to do it. I meant for you to use the first. I didn't even noticed that it had a manual way. I'm going to step out now. I just realized to many people helping can get confusing for someone.

llamakc knows what he's doing. From the advice he's given you so far, you're being served very well.

---

### Post by llamakc on 2007-01-24
> **ashmew2 said:**
> I think u shud get Limewire off [www.Limewire.com]("http://www.Limewire.com") or Limewire Pro of somewhere(AM i allowed to tell this here? ). I have a Limewire Pro setup.rpm which works fine on Edgy as well as Dapper Drake . ill tell u everything step by step if u havent yet figured out :D
By the way , Frostwire may be the blue clone of Limewire but i prefer LImewire :P Just my thoughts:D

OP will still need JAVA, which is where they are stuck. They've already installed Frostwire.

---

### Post by naruto650 on 2007-01-24
Ok so this is what i did. I have gone to system>adminstriation>synaptic then settings and did what u guys told me. I closed it and reloaded it. Afterwards i went to terminal and put this in 
sudo apt-get install sun-java5-jre i put my password and now it gave me this E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 
Im so confused and kinda mad. I think that xp was better, but i can't go back to itcause i don't know how to.

---

### Post by llamakc on 2007-01-24
> **naruto650 said:**
> Ok so this is what i did. I have gone to system>adminstriation>synaptic then settings and did what u guys told me. I closed it and reloaded it. Afterwards i went to terminal and put this in 
sudo apt-get install sun-java5-jre i put my password and now it gave me this E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 
Im so confused and kinda mad. I think that xp was better, but i can't go back to itcause i don't know how to.

You have only yourself to be angry with. You currently have Synaptic open, which stops you from using the commandline and executing those commands.

Close Synaptic and run the terminal commands again. See, you learned that only one process can access the dpkg system at a time. 

You've learned alot and are to be commended for your patience. However, if you want to go back to Windows I have no desire to help you any further. Sorry, but I'm ignorant of all things Windows.

You have more power at your fingertips right now than you realize.

---

### Post by naruto650 on 2007-01-24
> **llamakc said:**
> You have only yourself to be angry with. You currently have Synaptic open, which stops you from using the commandline and executing those commands.

Close Synaptic and run the terminal commands again. See, you learned that only one process can access the dpkg system at a time. 

You've learned alot and are to be commended for your patience. However, if you want to go back to Windows I have no desire to help you any further. Sorry, but I'm ignorant of all things Windows.

You have more power at your fingertips right now than you realize.

Well this is hard for me sense im new to this thats why. Well the only reason for windows was because i didn't have to do anything. lolz But i thank you all. It looks it worked. Thanks alot. And yes i've learned alot. Thanks again.

---

### Post by llamakc on 2007-01-24
> **naruto650 said:**
> Well this is hard for me sense im new to this thats why. Well the only reason for windows was because i didn't have to do anything. lolz But i thank you all. It looks it worked. Thanks alot. And yes i've learned alot. Thanks again.

Yay! Congrats, naruto. 

Check out that Dapper guide at [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) for any other questions you have.

Make sure to get your mp3's playing, and be able to view videos on the Web. Dont' forget to install Flash either.

Good job. I'm glad you hung in there.

---

### Post by naruto650 on 2007-01-24
Couldn't have done it with out you guys. Thanks alot again.

---

### Post by ashmew2 on 2007-01-25
haha i guess problem resolved!! :D

---

