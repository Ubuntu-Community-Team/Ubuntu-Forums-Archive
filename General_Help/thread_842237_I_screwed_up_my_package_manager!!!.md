---
title: "I screwed up my package manager!!!"
date: 2008-06-27
forum: General Help
---

### Post by impel on 2008-06-27
Hello everyone.

I'm brand new to Linux and so far I am loving my experience.  I just am not to hot on the terminal so I was glad to see a lot of installing can be done via package manager, but unfortunately I messed it up when attempting to enable more repositories.

Ubuntu 8.04

I was semi following directions on this site:
[http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html](http://linuxondesktop.blogspot.com/2007/07/35-cool-applications-to-install-on.html)

And ended up with this error now on package manager

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I'm not sure what needs to be changed or I would edit the file. Don't want to screw it up any further if I cant.

Please help!! Thanks.


Jason


PS. If anyone can guide me to an easier way to enable the repositories so installing apps is easy, that would be great.

PPS. I also having issue installing Adobe Air via .bin through terminal. it keeps telling me the file isn't there when it is? Is there any way to install a bin without terminal?

---

### Post by wormser on 2008-06-27
Post the results of the command.

```
gedit /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by impel on 2008-06-27
well, I figured out how to revert back the old list (i think).

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
sudo apt-get update
sudo apt-get upgrade

any suggestions on my other two problems? I know I should post in a different category. will do later.

---

### Post by wormser on 2008-06-27
> **impel said:**
> well, I figured out how to revert back the old list (i think).

sudo mv /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
sudo apt-get update
sudo apt-get upgrade

any suggestions on my other two problems? I know I should post in a different category. will do later.

That looks fine for getting rid of the error.  If you still want the Medibuntu repository follow the directions [here]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories").  The other repositories can be enabled in System> Administration> Software Sources.

You need to be in the same directory as the .bin to install it.  Read [How to Install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by drs305 on 2008-06-27
> **impel said:**
> 

PS. If anyone can guide me to an easier way to enable the repositories so installing apps is easy, that would be great.

PPS. I also having issue installing Adobe Air via .bin through terminal. it keeps telling me the file isn't there when it is? Is there any way to install a bin without terminal?


Jason, 

First, welcome to ubuntu. 

I looked at the link you provided and noticed the repositories were for fiesty. Since you just recently came to ubuntu it is likely you are running the hardy version. Repositories are specific to a given distribution, so if your repository list contains a reference to an earlier version you will get errors. For adding the medibuntu repository, the method recently changed. This is how you do it now if you are running Hardy:
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


As to installing apps from bin, the best advice is to try to get a package via synaptic or apt-get in the repositories. You can install apps packaged in bin files but these programs will not be updated or tracked via synaptic and can be difficult to uninstall. If you can't find a package and need to install via a bin file, here is a link on how to do it:
[How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

I got distracted while editing this post - wormser - are you my long lost twin?  ;-)

Added for wormser: My post was pretty much identical - sometimes my attempts at humor are a bit obtuse.

---

### Post by wormser on 2008-06-27
> **drs305 said:**
> I got distracted while editing this post - wormser - are you my long lost twin?  ;-)

Huh

---

### Post by impel on 2008-06-27
Thanks for responding.

I will check into the info on the repositories later because I need to install a few other apps I couldnt get on the package manager.

For the installing the .bin, I already read that how to install anything and thats why I didnt just try to always install .bin and such like the last time i gave linux a shot (2 years+ ago).

The file is on my desktop. I even right clicked on it and gave read/write permissions to everyone along with execute. I am opening terminal and navigating to /home/jason/Desktop/filename.bin and it is just telling me there is no file by that name. (not on the linux system now or I would copy exact message).

I'm trying to install Adobe Air for use with Twhirl and other possible apps. If this app is available through the additional repositories, I will just focus on that.

---

### Post by wormser on 2008-06-27
This blog should help. [How to Install Adobe AIR on Ubuntu]("http://www.sizlopedia.com/2008/04/06/how-to-install-adobe-air-on-ubuntu/")

---

### Post by oldos2er on 2008-06-27
Open a terminal. Type "cd Desktop" to get to your desktop directory. Then type "./filename.bin"

---

### Post by impel on 2008-06-28
Thanks. I ran that code that drs mentioned and a lot of stuff happened in the terminal, but I don't see any additional sources in synaptic package manager.

I wanted to download Opera, and a few other programs I heard of. I search Opera and it isn't there.

As for installing Adobe Air. That is the site I was following. Below I have pasted my results from terminal by trying to execute regularly like mentioned above and the chmod then sudo execute like mentioned in the how to. Both times I get a little different respons of no such file.

jason@JBOX:~$ cd Desktop
jason@JBOX:~/Desktop$ ./adobeair_linux_a1_033108.bin
bash: ./adobeair_linux_a1_033108.bin: No such file or directory
jason@JBOX:~/Desktop$ chmod +x adobeair_linux_a1_033108.bin
jason@JBOX:~/Desktop$ sudo ./adobeair_linux_a1_033108.bin
[sudo] password for jason: 
sudo: unable to execute ./adobeair_linux_a1_033108.bin: No such file or directory
jason@JBOX:~/Desktop$ 

The file is there and I have even viewed properties and copying the name and pasting it into the terminal to make sure it is exact.

---

### Post by oldos2er on 2008-06-28
All you need to do is type the first two or three letters of the file name, e.g. ado, then hit the Tab key for filename completion.

---

### Post by impel on 2008-06-28
still no luck.

I cd to desktop. typed ./ado then hit tab it filled it in. gives me error no such file or filename.

i just deleted the file. downloaded it again to the basic home directory, did chmod hen ./ on it and still same thing.

jason@JBOX:~$ wget [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)
--17:04:09--  [http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin](http://download.macromedia.com/pub/labs/air/linux/adobeair_linux_a1_033108.bin)
           => `adobeair_linux_a1_033108.bin'
Resolving download.macromedia.com... 72.246.147.191
Connecting to download.macromedia.com|72.246.147.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 15,847,512 (15M) [application/x-macbinary]

100%[====================================>] 15,847,512   269.84K/s    ETA 00:00

17:05:11 (248.26 KB/s) - `adobeair_linux_a1_033108.bin' saved [15847512/15847512]

jason@JBOX:~$ chmod +x adobeair_linux_a1_033108.bin 
jason@JBOX:~$ sudo ./adobeair_linux_a1_033108.bin 
[sudo] password for jason: 
sudo: unable to execute ./adobeair_linux_a1_033108.bin: No such file or directory
jason@JBOX:~$

---

### Post by wormser on 2008-06-28
Post the output of this command.  Make sure you are in the same directory.

```
ls -la ad*
```

---

### Post by impel on 2008-06-28
I should be in the same directory. I saw the file icon change from blank to the purple square when I did the chmod command.

here is the output:

jason@JBOX:~$ ls -la ad*
-rwxr-xr-x 1 jason jason 15847512 2008-03-25 17:37 adobeair_linux_a1_033108.bin
jason@JBOX:~$

---

