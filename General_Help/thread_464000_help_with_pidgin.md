---
title: "help with pidgin"
date: 2007-06-04
forum: General Help
---

### Post by Irti on 2007-06-04
i hav an amd 64 bit dual core 2 processor....so i installed a 64 bit version of ubuntu linux......i wanted to install pidgin...so i downloaded it...bt wen i try to install it....it says wrong architecture i386......from where do i download one for 64 bit...or is there sum way to gt arnd this problem

---

### Post by pay on 2007-06-04
You can either compile your own amd64 version of pidgin (recommened) or force the 32bit deb to install (not recommended with sudo dpkg -i --force-architecture pidgin*.deb

---

### Post by Irti on 2007-06-04
ok how do i compile a 64 bit version of pidgin........i am a very new linux user....hav bn using windows all my life.....pls help

---

### Post by pay on 2007-06-04
The way I would do it would be```
sudo aptitude install build-essential
sudo apt-get build-dep gaim
cd /usr/local/src
sudo wget http://puzzle.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.1.tar.bz2
sudo tar jxvf pidgin-2.0.1.tar.bz2
cd pidgin*
./configure --help
sudo ./configure --with-x 
sudo make
sudo make install
```

---

### Post by Irti on 2007-06-04
ok i just pasted ur commands...and whoa...sumthin sumthin hapened......it downloaded sumthin and installed sumthin...nd i dont hav ne idea wut hapened....so how do i run pidgin now....is it installed?? wut do i do now..??

---

### Post by pay on 2007-06-04
If it didn't have any errors then it should have been installed. Look in Applications > Internet. Or type in pidgin into the terminal. If that doesn't work then something has gone wrong.

---

### Post by Irti on 2007-06-04
ok i think sumthin has gone wrong coz i cant find it newhere

---

### Post by Irti on 2007-06-04
ok i tried typin out all the commands...............it says invalid operation build.....for sudo apt-get build-deb gaim.............

---

### Post by pay on 2007-06-04
do ```
sudo ./configure --with-x 
sudo make
sudo make install
```and see if any errors come up. If they do then post the error.

---

### Post by loathsome on 2007-06-04
Just download [Pidgin](http://pidgin.im), and compile it with [COLOR="DarkSlateGray"]**./configure**[/COLOR]. Make sure you've got the required libraries (if not, the configuration script will tell you which ones you're missing, and you can download them from synaptic).

After you've ran configure, do a [COLOR="DarkSlateGray"]**$ make**[/COLOR] followed by **[COLOR="DarkSlateGray"]$ sudo make install[/COLOR]**
Now you can launch Pidgin by pressing ALT + F2 and type «pidgin»

Good luck.

---

### Post by Irti on 2007-06-04
ok it says................."   ./configure: command not found"

---

### Post by loathsome on 2007-06-04
Hmm. Are you in the right directory? Because ./configure **surely** does exist ;)

---

### Post by Irti on 2007-06-04
ok which directory do i hav to be in........the pidgin file tht i downloaded is on my desktop.......and wen i open the terminal i just typed in the command straight away...(irti@irti:desktop)thts supposed to b the desktop directory right???

---

### Post by loathsome on 2007-06-04
> **Irti said:**
> ok which directory do i hav to be in........the pidgin file tht i downloaded is on my desktop.......and wen i open the terminal i just typed in the command straight away...(irti@irti:desktop)thts supposed to b the desktop directory right???
You need to extract the archive (.tar.gz), and then go to the directory in the terminal.

Take a look at this guide:
»» [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Irti on 2007-06-04
ok the thing is this....its not a tar.gz file its a .deb file................wut do i do now

---

### Post by loathsome on 2007-06-04
> **Irti said:**
> ok the thing is this....its not a tar.gz file its a .deb file................wut do i do now
Read my post on the previous page - You didn't download from where I told you to.

---

### Post by Irti on 2007-06-04
ok ****....ya u r right dude...thanx a lot mn...sry for bein such a dumbass.......

---

### Post by loathsome on 2007-06-04
No no, everybody's got to start somewhere ;)

I'll be happy to help you further.

---

### Post by Irti on 2007-06-05
hey i gt everythin rite.....its workin like a charm...thanx a lot....though there is one more problem......it says that i need ssl supported library to login to msn ...and a tsl supported library to login on googletalk......i installed all the ssl and tsl named updates from synaptics...bt still am gettin nowhere....cud u plzzzzzzzzzzzzz help me with this????????

---

### Post by loathsome on 2007-06-05
Yes, you'll ned to do a **[COLOR="DarkSlateGray"]$ sudo apt-get install gnutls-dev[/COLOR]** and then recompile Pidgin just like you did the first time.

Glad to hear you got it working! :)

---

### Post by frolle on 2007-06-05
> **pay said:**
> The way I would do it would be```
sudo aptitude install build-essential
sudo apt-get build-dep gaim
cd /usr/local/src
sudo wget http://puzzle.dl.sourceforge.net/sourceforge/pidgin/pidgin-2.0.1.tar.bz2
sudo tar jxvf pidgin-2.0.1.tar.bz2
cd pidgin*
./configure --help
sudo ./configure --with-x 
sudo make
sudo make install
```

Cheers :) Got it working..

---

### Post by Irti on 2007-06-05
@ loathsome..................dude wut can i say............u r my superman.....u saved the day....(again).............................@ frolle....thanz a lot for helpin out man....bt i just tried loathsome's method first and it worked...thanx a lot neways................

---

### Post by Irti on 2007-06-05
dude do u hav ne idea how do i go about installin wine...............???? and can i play games on linux???.....like test drive unlimited and all tht......(i just cant get over playin games on the comp man)..................................

---

### Post by loathsome on 2007-06-06
> **Irti said:**
> @ loathsome..................dude wut can i say............u r my superman.....u saved the day....(again).............................@ frolle....thanz a lot for helpin out man....bt i just tried loathsome's method first and it worked...thanx a lot neways................

:lolflag: Thanks! I'm always happy to help out fellow Ubuntuers ;)

> **Irti said:**
> dude do u hav ne idea how do i go about installin wine...............???? and can i play games on linux???.....like test drive unlimited and all tht......(i just cant get over playin games on the comp man)..................................

Installing wine is incredible easy. Just open up your terminal and run [COLOR="DarkSlateGray"]**$ sudo apt-get install wine**[/COLOR] - now you can start (almost) any Windows application by typing [COLOR="DarkSlateGray"]**$ wine myfile.exe**[/COLOR].

Yeah, you can play some games. Don't know about Test Drive, though - You might want to try Cedega for that, but that's a commercial product and is not free.

I'm playing Half-Life 2 (and Episode 2 as well) perfectly through Wine, so .. I can't guarantee anything, just give it a try!

Also remember that there's lots of **free**, fun and Linux-only games out there. You can find them everywhere. There's quite a few under "add/remove programs" too.

edit; I almost forgot - I've compiled and built two games into a debian package, which you can find in my signature ;) Just download and double-click them to launch.

Have fun.

---

### Post by Irti on 2007-06-06
niceeeeeeeeeeeee!!!!!!!!!!!! wine workin tooooo..........ok dude tell me where do i gt the games u made...really wana try them........nd test drive unlimited not workin.....am tryin to get cedega though  ;) ...............ok wanted to ask u sum more stuff man........is there any media player in ubuntu...tht luks gud and does the work too......(u know sumthin like wut the media player was in xp....or even itunes)............and i downloaded vlc media player.....bt the audio is totally screwed...........my speakers start crackling......wen the same videos were playin fine in xp...is it bcoz of video or audio codecs??????????................o ya one more thing...............i installed the 32 bit firefox...for 64 bit amd...(as i hav a 64 bit amd dual core 2 processor with a 64 bit version of ubuntu running)..........bt i dont like the idea sumhow..........how can i uninstall the 32 bit firefox??? it doesnt show up in the add remove thingy..................and is there any other way to gt flash plugins for 64 bit firefox????

---

### Post by Irti on 2007-06-06
test drive not workin on cedega either....so guess i'll just hav to reboot whenever i wanna play it.........

---

### Post by BrokeBody on 2007-06-06
> **Irti said:**
> i hav an amd 64 bit dual core 2 processor....so i installed a 64 bit version of ubuntu linux......i wanted to install pidgin...so i downloaded it...bt wen i try to install it....it says wrong architecture i386......from where do i download one for 64 bit...or is there sum way to gt arnd this problem

Well, you already solved your problem, but in the case that you format your hard drive and install Ubuntu again, you can simply download 64bit version of Pidgin from [here](http://www.getdeb.net/download.php?release=956&fpos=0). Just double click on the package, click on Install and that's it. ;)

---

### Post by cstudent on 2007-06-06
You could just download the .deb from getdeb.

[http://www.getdeb.net/search.php?keywords=pidgin](http://www.getdeb.net/search.php?keywords=pidgin)

---

### Post by Neatchee on 2007-07-14
Michael Trausch and I have been working on backporting Pidgin for Feisty.  He works on the 32bit releases, and I do the 64bit releases.  The advantage to our backports is that they appropriately match a base install of Feisty, and also have working backports of OTR (Off-the-Record messaging) and Guifications.

You can download our backports here:  [http://www.trausch.us/pidgin](http://www.trausch.us/pidgin)  They are incredibly easy to use!  Enjoy!

---

### Post by fd0man on 2007-08-02
Pidgin 2.1.0 is out, and we've updated our release for that.

Visit [http://www.trausch.us/pidgin/](http://www.trausch.us/pidgin/) for the information.  We now have an APT repository so that you don't have to do (almost) anything manually.  Enjoy!

---

