---
title: "Noob needs help (please help)"
date: 2007-01-02
forum: General Help
---

### Post by Metalclay on 2007-01-02
i'm completely new to ubuntu, actually...to linux in general. i wanted to work with ubuntu to get familiar with terminals and everything linux since ubuntu has gui and everything.

so...everything seems fine, to my surprise, all i did was install the cd and everything looks fine.

but..i can't connect to the internet! i have so many more problems (i think) but...i can just research that on google later. right now my main concern is the internet. i have a broadcom wireless card in my laptop. i've searched through these threads...but...i just can't make sense out of anything. i've spent a whole two days researching this...so i just gave up and decided to register to these forums.

so...my question is...how can i get it to work? right now i'm using wired connection to type this...but i need wireless seeing as how my sister uses this wired connection.

anyway from what i've read i need to install some bcm43xx thing? then i have to enter a pass word? well...terminal won't let me enter a password :(  i am completely stuck. since i grew up on windoze i have nothing to help me out. so...can anyone help me? please! in the meantime i'll be researching more. but...if i can't find anything i'll just go back to windowze...which i don't want to i want to get used to this :D

---

### Post by lilmienboy on 2007-01-02
check this site [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html)
this is what i did to work my wireless

---

### Post by hashimoto on 2007-01-02
> **Metalclay said:**
> anyway from what i've read i need to install some bcm43xx thing? then i have to enter a pass word? well...terminal won't let me enter a password :(  

Metalclay, when you install programs or otherwise administer your system in terminal, you need to get super user rights. This is done by adding "sudo" in  front of the command. Your system will then ask for your user password. However, when you write your password, terminal does not show any asterix or like instead of the password. The row just stays blank. Don't worry, hit enter after the password and things should be fine.

---

### Post by Metalclay on 2007-01-02
thanks all. i tried to put in the password that the guide told me to enter "y" and it turns out, it just needs my admin passoword. anyway, even with that it didn't work. here's what i got after entering password (at least something happened):

iggy@Iggy-laptop:~$ sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta.o
bcm43xx-fwcutter can cut the firmware out of /home/iggy/Desktop/wl_apsta.o

  filename :  wl_apsta.o
  version  :  3.130.20.0
  MD5      :  e08665c5c5b66beb9c3b2dd54aa80cb3

extracting bcm43xx_microcode2.fw ...
extracting bcm43xx_microcode4.fw ...
extracting bcm43xx_microcode5.fw ...
extracting bcm43xx_microcode11.fw ...
*****: Sorry, it's not possible to extract "bcm43xx_microcode13.fw".
*****: Extracting firmware from an old driver is bad. Choose a more recent one.
*****: Luckily bcm43xx driver doesn't include microcode11 uploads at the moment.
*****: But this can be added in the future...
extracting bcm43xx_pcm4.fw ...
extracting bcm43xx_pcm5.fw ...
extracting bcm43xx_initval01.fw ...
extracting bcm43xx_initval02.fw ...
extracting bcm43xx_initval03.fw ...
extracting bcm43xx_initval04.fw ...
extracting bcm43xx_initval05.fw ...
extracting bcm43xx_initval06.fw ...
extracting bcm43xx_initval07.fw ...
extracting bcm43xx_initval08.fw ...
extracting bcm43xx_initval09.fw ...
extracting bcm43xx_initval10.fw ...

wl_apsta is the file i was told to dl. also, it said something that if it doesn't work i can use my own driver...but my driver is an exe file...i thought linux couldn't read that.

@lilmienboy

when i  "Create a file called /etc/default/wpasupplicant, add entry ENABLED=0 and save the file" where do i save it? i saved it to my documents "iggy"-my name. and...it said i don't have permission to save file. which is untrue, because i'm admin. 

so far though...i think it's working, when i tried to run the command (next step) "touch-something" i got a return that read that file doesn't exist....so...i just need to know where to save. and if there's a specific place....how do i type it in? i can't find a place to type something like c:/windows/system32. all i can find when  save the file, are iggy, documents, and file system. 

oh...and the way i'm saving the file is...i just opened "text editor" typed in "ENABLED=0". i tried saving it to folder "iggy"-my name. and i named the "file /etc/default/wpasupplicant", but i something that said i needed permission. also, if i name it 'untitled document' it saves fine. so...if i do need permission...how do i get it? i'm already logged in as "iggy" and i'm the admin. do i need to enter "admin" at the login screen, and enter it as that?

xD, thanks for any help. sorry i'm such a noob. but...i just need this very badly. everything i know about computers is through googling xD so....without google, i'm very limited.

---

### Post by lilmienboy on 2007-01-02
the files name is wpasupplicant, what i did was save it to the desktop and than i move the file 
with the terminal.  like this.

cd                                                       
cd Desktop                                       
sudo mv wpasupplicant /etc/default/wpasupplicant               

and thats shoulld move that file to that folder without any message

and when they mean "comment" everything except the lo they want you to put "#" this b4 the line
ex:
# this line is comment

let me know if this work, because im still a noob just getting to know everything.

---

### Post by lilmienboy on 2007-01-02
i

---

### Post by Metalclay on 2007-01-02
sweet! it worked! i did up to this:

To update the source list run the following command

sudo apt-get

sudo apt-get install wpasupplicant

sudo apt-get install network-manager-gnome network-manager

sudo gedit /etc/network/interfaces

and it worked. all it needed was a restart. thank you lilmienboy! *bookmarks page* hope all my difficulties can be solved easily as this :D i just now i'm gonna be back here xD. w/e everyone starts some where;)

---

