---
title: "someone owns my file &amp; i want it back. help please"
date: 2007-06-15
forum: General Help
---

### Post by evotux on 2007-06-15
hello,

i will start by saying im either stupid , very tired, but here is my problem.

how do i get permission to write and save my sources.list file, im trying to install automatix2.

i have spent about 9 hours trying to chown, chmod and all that but am going round in circles, so as a end result i need some help if possible.

when i log into a terminal it starts as

mumbo@mumbo- laptop:~$    after this i tried to do all sorts but to no avai.

so did some reading and tried to log in to root, when logging into root i have

root@mumbo- laptop:/home/mumbo   i tried to change sources list , no permissions or i dont own this file,or this file does not exist, tried chmod, chown ect to no avail as i must be slow or dont understand what people are actually getting at.

then i went to root@mumbo- laptop:~#   still cant change file 

can anyone tell me in a really simple way how to do all this chown , chmod what user or group i have to use i dont even know what user or group i am, ( i pressume im user mumbo, but as for group , no idea) do i have to add mumbo to a group in groups and users or am i there al ready.

i have read lots on chmod and chown but i cant seem to get it to work, BUGGER, sorry just a frustration scream.

i have tried chmod then chown ,gedit gksudo is there a order to put them in , since ive done so much im lost to where im going over the same again and again.

have tried 

gksudo , gedit but am i having all the /ect/apt/sources.list if needed in the right order.

any help appreciated , have tried chown --help ect but man there is no real visual example to get me some sanity.

evotux

---

### Post by jasonlfunk on 2007-06-15
Mine is this:
-rw-r--r-- 1 root root 1810 2007-05-02 22:22 sources.list

So as root, do 
```
chown root.root sources.list
```
then
```
chmod 644 sources.list
```

---

### Post by mvaniersel on 2007-06-15
Hi

The simplest way is to open a terminal  (as normal user!) and type:

gksudo gedit /etc/apt/sources.list

This should open the editor and you should be able to make modifications and save them. No other commands are necessary.

There is never need to chmod / chown configuration files. On a default installation, the permissions on those files are set correctly and they should always be owned by root. No need to chmod chown at all.

---

### Post by evotux on 2007-06-15
Hello nand thanxs for the help,

Unfortunately i go to the file paste in a sources.list generated file , the right one in hope.

but where do i save the file to, try to save it says does not exist, so try save as do i save in the root file or mumbo ?( my user name ) or in file system (my partition , i only have one partition)

i assume ( but assumption is the mother of all &^%$ ups) to save it in the users name mumbo that comes up, or is it filesystem or root.


then when i open sources.list again there is nothing in it through terminal, i can view i can view a file sources.list through computer.

i now have a few sources.list files sone normal anme and others with ~ after, so i try again and save then go to close then it says in popup you have to save so i save and it says cannot save no file found.


i seem to have tried to save in all at some stage to get it right, is there nothing in the sources file to start with should i go and delete them all and start again, also have gpg.asc files in ect/apt/ file and as mumbo user, and in the root file, yeah i know im a nightmare, all i want to do is add automatix2, 

i havnt added any of the 145 updates available as im not sure what ones to add, is this a problem.


shoot me now, thanxs evotux

---

### Post by southernman on 2007-06-15
push your keyboard away and go take a nap. ;) jk

---

### Post by smoker on 2007-06-15
can you explain what you want to do with your sources list? if it is to add a repository, i think the easiest way, if your using fiesty, is to click, system, administration, software sources, and click the 'third party software' tab, and you can use the 'add' button.

as for installing automatix, there is an easy to follow guide here:
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

best of luck

---

### Post by evotux on 2007-06-16
howdy smoker , i think i dont know what im trying to do either.

it has to do with the sources.list file in /ect/apt in trying to install automatix2, i will go to the link provided and download the deb file and try that,

BUT, when it says open the sources file and add : deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
to the sources file, when i open the file with gksudo gedit /ect/apt/sources.list file in terminal, there is nothing in it, if i go to places-computer-file system ect-apt folder ther is a sources file in there with stuff in it from all the updates ect.

can you explain why it is empty in terminal and not in gui, and if i try to edit the file i get you do not have permissions.

should i 

a: go to terminal in root: root@hypertech:~$/home/mumbo# tried still empty when opened in terminal

b:chmod sources .list file ,  in root or user ( mumbo)

c:or do i open in terminal then select the open button on interface ( just tried this , seemed to work ) and then edit and save, in the gui platform, this appeared to work should i keep going fromthe dapper drake install ,[http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu:::](http://ubuntuguide.org/wiki/Dapper#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu:::) 

or am i better to use the link you sent me from the ::  First Step: 

 echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main" | sudo tee -a /etc/apt/sources.list
so many options so little time

i will try the link if not will go and sleep on it.

thanxs smoker, i will get there in the end very determined

---

### Post by DagMan on 2007-06-16
Hi,
If it's a 32 bit install of Ubuntu Feisty, do the following to install Automatix

```
wget  http://www.getautomatix.com/apt/dists/feisty/main/binary-i386/automatix2_1.1-4.6-7.04feisty_i386.deb
sudo apt-get install python2.4
sudo dpkg -i automatix*deb ; rm automatix*deb
```

That should work I believe, and automatix would appear in the menu or if not then you can type automatix2 in a terminal.
When Automatix runs, it will both add itself to your sources.list file and add a create a decent set of software repositories if you don't already have them.

To edit the sources.list file tough, and add that line like you wanted, you would do this and this is where your sources list file is located that you're looking for:
```
sudo gedit /etc/apt/sources.list
```
Then add the line.

Good luck

Edit, didn't see the post above... that too looks that it would solve your problem.

---

### Post by smoker on 2007-06-16
> BUT, when it says open the sources file and add : deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main
to the sources file, when i open the file with gksudo gedit /ect/apt/sources.list file in terminal, there is nothing in it, if i go to places-computer-file system ect-apt folder ther is a sources file in there with stuff in it from all the updates ect.

hi, evotux, there should be no need to edit your sources list, i believe automatix will do that for you as it installs, or when it is run for the first time (it's a while since i've done this, but i don't remember ever having to manually edit the sources list!)

i would download the correct deb from the link i gave you (you have dapper?) then follow the guide pertaining to that version, that is opening a terminal, and copying each command one at a time, pasting the command at the terminal prompt, and pressing enter after each.

i would leave the sources file alone, at the moment, and try to install automatix first. if you still get problems please post back,

best of luck,

---

### Post by longlegs on 2007-06-16
sudo gedit /etc/apt/sources.list         NOT NOT NOT
sudo gedit /ect/apt/sources.list

Have a good day!
longlegs

---

### Post by evotux on 2007-06-17
AAAAAHHHH  AAAAHHHH   DOH

thanxs longlegs i should shoot myself, will have to dounle check the file name, sometimes i truly wonder about myself .

cheers , bugger im laughing at myself right now and my wife has just slapped me around the ears

---

### Post by MimeyNaomi on 2007-07-11
I'm having the same problem; trying to follow the instructions on enabling multimedia in Feisty [the pinned thread in Multimedia and Video] since I can't play DVDs using any media player I have, and I've tried several.

I try to add the Medibuntu repository, but it doesn't give me permission to save.

Since I can't reply to the pinned topic, I'll ask it here, but I have to know either how to change the permissions or install Medibuntu some other way.  Unless there's something completely different that's keeping me from playing DVDs, in which case I'd love a suggestion.

Edit:  NEVER MIND!  Got it, thanx anyway

---

