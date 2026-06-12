---
title: "Can't install zsync via trial bootup of Ubuntu 14.04.1 LTS"
date: 2015-08-01
forum: General Help
---

### Post by G_Blackburn on 2015-08-01
Trying to update my old iso image of Ubuntu via bootable trial mode of Ubuntu 14.04.1 LTS

I open the Terminal and try to install zsync by typing 

 sudo apt-get install zsync -y

and get error message.  Here the full text from the terminal


ubuntu@ubuntu:~$ sudo apt-get install zsync -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package zsync


How do I install zsync :(

---

### Post by deadflowr on 2015-08-02
You need to make sure the universe repository is enabled, and then you need to run an apt-get update to ensure you connect to the proper packages.

---

### Post by G_Blackburn on 2015-08-02
Thanks for that info.  I did not understand what repository was but You put me on the right path and after I did a google. :D  

I found this which I believe is the answer.

[h=3]To enable main repository,[/h]sudo add-apt-repository main
[h=3]To enable universe repository,[/h]sudo add-apt-repository universe


[COLOR=#111111][FONT=Ubuntu]**NOTE:**[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After enabling the repositories, don't forget to update it.Run the below command to update the repositories,[/FONT][/COLOR]
sudo apt-get update

---

### Post by G_Blackburn on 2015-08-02
I seem to have installed zsync via  terminal commands but now I am stuck not able to get iso image updated.

I have tried following 

zsync -i /media/ubuntu/BOX 3/UBUNTU-Old-Version 14.04.1-64bit.iso [http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync](http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync)

"BOX 3" being the name of the partition where I have the iso image stored which is called "UBUNTU-Old-Version 14.04.1-64bit.iso"

What am I doing wrong?

It could be that I have not enough space on the linux trial mode as I only made it with about 150mb free  space.  Where would the newly created iso be made.  On my hard drive or on the flash card where ubuntu resides?

---

### Post by howefield on 2015-08-02
Could be the spaces in your path to the iso.

Try running the command from the folder that you have stored the iso.

As an example, for me to update the development iso, the commands would look like this..

```
cd /Data/Wily\ Werewolf
```
```
zsync http://cdimage.ubuntu.com/daily-live/pending/wily-desktop-amd64.iso.zsync
```

For ease, I also name the iso on my machine to correspond with the downloaded file.

---

### Post by G_Blackburn on 2015-08-02
Not having much luck.  I tried cd /BOX 3   which is the partion wher the iso file situated but got No such file or directory.  I don't have it in a directory it on the root of the partition called "BOX 3" to make life simple.

I then tried the following which was also unsuccessful. :(


I renamed the file to old.iso and copied to the ubuntu desktop
then tried updating and it tried to download the whole file which is not what I want.

text in terminal as follows;

ubuntu@ubuntu:/$ cd $HOME/Desktop
ubuntu@ubuntu:~/Desktop$ zsync -i /Desktop$/old.iso [http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync](http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync)
#################### 100.0% 412.1 kBps DONE     

open: No such file or directory
not using seed file /Desktop$/old.iso
Read /Desktop$/old.iso. Target 0.0% complete.      
No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from [http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso:](http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso:)


I may just download the whole iso again with my limited bandwidth which is not what I want to do as would prefer just updating the changes to the iso file. :(

---

### Post by howefield on 2015-08-02
You would need to escape the space in BOX 3 by using a backslash, like

```
/media/ubuntu/BOX\ 3/
```

And rename your existing iso to match the one you are downloading, ie, ubuntu-14.04.2-desktop-amd64.iso.

There is something very simple here that is preventing you, stay with it :)

---

### Post by G_Blackburn on 2015-08-02
The update succeeded I think.  I kept the old iso image on ubuntu desktop and renamed it same as one I wanted to amend from the web address.  But when I check the old iso image with properties still states it's the same size?  confused!

Here's the output from the terminal showing it updated successfully.  So now question is where is the new updated iso stored?



ubuntu@ubuntu:~$ zsync -i /home/ubuntu/Desktop/ubuntu-14.04.2-desktop-amd64.iso [http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync](http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso.zsync)
#################### 100.0% 193.5 kBps DONE     

reading seed file /home/ubuntu/Desktop/ubuntu-14.04.2-desktop-amd64.iso: *******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read /home/ubuntu/Desktop/ubuntu-14.04.2-desktop-amd64.iso. Target 57.3% complete.      
downloading from [http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso:](http://www.mirrorservice.org/sites/releases.ubuntu.com/14.04.2/ubuntu-14.04.2-desktop-amd64.iso:)
###########--------- 57.3% 2.9 kBps         
#################### 100.0% 600.3 kBps DONE

---

### Post by VMC on 2015-08-02
At the end it should have stated that the sums checked okay. I don't see that.

---

### Post by G_Blackburn on 2015-08-02
There were one or two lines that I could not copy and paste from the terminal at the very end.  Don't recall what now but don't remember any errors reported.  The old iso should have changed size? :(


I have given up now. :(

I can't afford to wasted more bandwidth trying as will end up using more bandwidth than downloading the whole iso image.  

I'm just wasting hours of my life away reading how to type correct commands into a terminal just to perform a simple task which could be done easy with a windows type software.

I only want Ubuntu as a more secure method for internet access and not to learn Linux and go back in time to the stone age methods of typing in commands when windows software could make the task simple!

---

### Post by VMC on 2015-08-03
You could open the iso using archive manager, then open the text file under "/.disk/info" , to see what date it shows at the far right.

---

