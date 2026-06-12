---
title: "SABnzbd for Linux"
date: 2007-02-24
forum: General Help
---

### Post by Martje_001 on 2007-02-24
Hi,
Since 29 March 2008 I provide .deb-packages. [This]("http://www.xs4all.nl/~mgj1/sabnzbd.htm") is the page where I keep updates of SABnzbd, and where you can download it (incl. older versions).

[B]Note: If you want to make SABnzbd accesable for all hosts, you should change *host = localhost* to *host = 0.0.0.0* in you *SABnzbd.ini*.
[/B]

Martje_001

---

### Post by felker2 on 2007-02-26
Good work!

Some remarks:
- username can be found via `whoami`
- some error checking on retrieval and installation of software would be nice
- if based on jtt1560's work, giving credits to him/her in the script would ne nice

I'll now test it to see if it works.

---

### Post by stonhaus on 2007-02-28
The links for the script to the [http://www.xs4all.nl/~mgj1/SABnzbd%204%20linux/](http://www.xs4all.nl/~mgj1/SABnzbd%204%20linux/) directory don't seem to be valid.

I tried pasting them into firefox, but got the same errors.

Any chance we could get them back up? 

Thanks.

---

### Post by Martje_001 on 2007-03-03
Sorry it is: [http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/](http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/)

And yes, it is based on jtt1560's work. I will put his name into the program :).
But jtt1560's work was not perfect, so I had to change many ;).
And I will experiment with 'whoami'.

I'm going to remove the ads too btw...

grz,
mart

---

### Post by gurgle on 2007-03-05
/home/evan/.SABnzbd.sh: 12: ./SABnzbd.py: not found

---

### Post by Martje_001 on 2007-03-06
I will look at it. Within 24 hours I've solved it. I promis:)

---

### Post by gurgle on 2007-03-07
^^ thanks, i appreciate it.

---

### Post by Martje_001 on 2007-03-09
It works fine here, even from a live-cd :confused: .
Are you sure you have done the 'sed'-step OK?

I'm not sure but maby this solves it:
```
cd ~/.SABnzbd/sabnzbd
wget -c http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/SABnzbd.py
cd ~/.SABnzbd/sabnzbd/templates
wget -c http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/templates.tar.gz
tar -xzvf templates.tar.gz
cd ~
wget -c http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/.SABnzbd.sh
cd ~/.SABnzbd/sabnzbd/
wget -c http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/SABnzbd.ini
cd ~/.SABnzbd/sabnzbd
chmod +x SABnzbd.py
sed -i -re 's/1234567/[SIZE="4"]**YOURUSERNAME**[/SIZE]/' ~/.SABnzbd/sabnzbd/SABnzbd.py
```

---

### Post by nikopol on 2007-03-10
Seems to work fine but I don't seem to be able to delete the servers that are initially setup apart from hacking at the .ini file.

nice piece of work - thanks.

---

### Post by Martje_001 on 2007-03-10
> **nikopol said:**
> Seems to work fine but I don't seem to be able to delete the servers that are initially setup apart from hacking at the .ini file.

nice piece of work - thanks.
Is correct. I have to change the source for this :( .
Next week it's ready I think ;)

---

### Post by Martje_001 on 2007-03-11
[SIZE="4"]**Update:**[/SIZE]
You now only have to type sabnzbd into your terminal to start SABnzbd!

[SIZE="4"]**To do:**[/SIZE]
If you have clicked on an ad, the ads disappear :).

---

### Post by gurgle on 2007-03-11
I tried this but I am getting teh same error. Is there any way to remove sabnzbd and then try again?

---

### Post by Martje_001 on 2007-03-12
Of course: 
```
rm -r ~/.SABnzbd
rm -r ~/.SABnzbd.sh
```

Follow the new instructions @: [SABnzbd for Linux]("http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/")

---

### Post by gurgle on 2007-03-12
^^ got it to work, thank you.

Looks like your version of the unrar tool is out of date though - would it be ok to upgrade to the new version?

---

### Post by Martje_001 on 2007-03-13
It's ok. But if I install SABnzbd with the newer version of unrar, it gives me an error ;)
But updating is OK, it works fine after :)

---

### Post by Martje_001 on 2007-03-31
I've removed the ads and made a new interface. See the screenshots below.
[[IMG]http://img382.imageshack.us/img382/7779/schermafdruknz8.th.png[/IMG]](http://img382.imageshack.us/my.php?image=schermafdruknz8.png)[[IMG]http://img118.imageshack.us/img118/8863/schermafdruk1xg0.th.png[/IMG]](http://img118.imageshack.us/my.php?image=schermafdruk1xg0.png)

What do you think of the new interface?

---

### Post by rookieone on 2007-04-10
I'm all for people putting together packages that make installing software like SABNZBD (with it's dependecies) easier but I don't like your way of doing that.
Your shellscript that downloads some template I don't neccessarily like, the sabnzbd alias that I can't get rid of anymore, the fact that you had ADS in your template to begin with even though all you did was bundle some free software ...

Thanks but no thanks

EDIT:

If you want to completely remove it you need to sudo rm two files /usr/bin/sabnzbd and /usr/bin/SABnzbd

---

### Post by Martje_001 on 2007-04-10
I've deleted my interface, and replaced it with the old one. OK?

---

### Post by gurgle on 2007-04-11
I agree with the ADs part too. It would probably just work better to include the NOVA interface, that works well for me.

---

### Post by pirothezero on 2007-04-11
the only issues I have with sabnzbd is that it shutsdown whenever it wants. In kde I had to setup a cron job and run a bash script to start it every 2 hours.

I moved over to gnome a while back and still haven't figured out how to run my bash script every 2 hours with a gui cron like option screen.

---

### Post by nosscire on 2007-04-12
Thanks! Have been trying to install this for quite a while now, but couldn't get it to work.. Worked just perfectly with your bundle :)

---

### Post by jtt1560 on 2007-04-12
Martje_001,

Thank you for taking my project and making it more robust. Good job! I was going to change some of my work to add the checkinstall package instead of the make install commands. This would allow for a complete uninstall through Synaptic Package Manager. You may want to consider it. You may also want to consider a choice in your script to keep the original interface and removal of the ads.

Keep up the good work. 

jtt1560

---

### Post by jimmsta on 2007-04-16
It seems to no longer work after a reboot. I -did- update unrar to the latest release (using Feisty Fawn). The web interface does not load up, even after executing sabnzbd... :(

Otherwise, it's a great script, and works pretty well... that is, if I can get it working again. :)

---

### Post by Martje_001 on 2007-04-23
> **jtt1560 said:**
> Martje_001,

Thank you for taking my project and making it more robust. Good job! I was going to change some of my work to add the checkinstall package instead of the make install commands. This would allow for a complete uninstall through Synaptic Package Manager. You may want to consider it. You may also want to consider a choice in your script to keep the original interface and removal of the ads.

Keep up the good work. 

jtt1560
I'm busy writing a second script which installs easier and works on Feisty. Checkinstall is a very good idea btw, but I don't know how to create such packages, so I'll keep the script ;)

---

### Post by frolle on 2007-04-23
Seems like some piece of work! I havn't tried it, but i think i will later.

---

### Post by Martje_001 on 2007-04-26
I've made the installer graphical, and it's working on Feisty Fawn! But how do you say in English 'you write something on your keyboard'? Type? Tape? :confused: :oops:

Later I'll put the names, in the script, of the ones that have helped me with the script...
(This version is btw completely non-ads :P)

[SIZE="1"]But now I'm going to my girlfriend[/SIZE]

---

### Post by jimmsta on 2007-04-29
It would be great if you added a wizard to setup the download directory and servers upon first install. I seem to have some strange problems, where as soon as I change the download directory, SAB stops working entirely, and I get a "500 Internal error" from the CherryPy server.

---

### Post by Martje_001 on 2007-04-30
Hmmmm.... Same problem here :P, I will add a setup wizard!

---

### Post by Kasper42 on 2007-05-04
Hi

I installed the script from the directions but when I run "SABnzbd" in the terminal, I get the following error.

> /usr/bin/SABnzbd: ./SABnzbd.py: /home/kasper/.SABnzbd/bin/python: bad interpreter: No such file or directory

Thanks :D

---

### Post by Martje_001 on 2007-05-05
This error appears when you've updated your system (unrar), when the script was running. Please do it again, but do NOT update.

Edit: You can update it after the script is finished

---

### Post by Kasper42 on 2007-05-05
Thanks Martje, I did downgrade unrar to the older version through Synaptic. I then removed all of SABnzbd and reinstalled it via the script. It now works great :D

---

### Post by Merijn on 2007-05-06
thank you.
it works fine for me. sabnzbd is the best newsgrabber.

bye
Merijn

---

### Post by REDISISTone.nl on 2007-06-02
Hi!

I'm trying to get it to work, downloaded the file, set the permission, dubble click, execute...but nothing happens...

What am I doing wrong ?

/EDIT

I executed the file in the terminal and I get the message that there is no authenication for the files:
libgtk1.2-common libglib1.2 libgtk1.2 xdialog

Tips?

---

### Post by Martje_001 on 2007-06-02
Strange... they should have a key in synaptic. But... You can do in a terminal:
```
sudo apt-get install xdialog
```
and answer al questions with yes (2 questions I think). Execute the script again and it should work.

---

### Post by REDISISTone.nl on 2007-06-04
Awsome!! It worked :) thanx !!:p

---

### Post by LightningCrash on 2007-06-20
> **pirothezero said:**
> the only issues I have with sabnzbd is that it shutsdown whenever it wants. In kde I had to setup a cron job and run a bash script to start it every 2 hours.

I moved over to gnome a while back and still haven't figured out how to run my bash script every 2 hours with a gui cron like option screen.

KAlarm will still run under Gnome, and it can do what you ask.

I use it to fire up XMMS as my alarm clock :)

---

### Post by stonhaus on 2007-06-25
Anyone have any luck getting the RSS feature installed? 

I have had it setup on a Windows box previously. I installed the python-feedparser (universal feedparser) from the repos, but no luck. I still get the feedparser module missing error on the RSS tab.

---

### Post by gurgle on 2007-07-05
RSS is not working for me either.

---

### Post by schrombot on 2007-08-28
Just posting to say that it worked great for me! My only problem is I have to run it with sudo, but that is no big deal. Thank a lot!

---

### Post by straydog50 on 2007-09-01
Hi there

I'm also trying to get Sabnzb working on Unbuntu Linux ( first of all much respect for builing this package =D> ) It's easy to install, and after a phew up and downs I have it working. I'm only sitting with one problem. In the config menu file: servers there are already two newservers filled in. I have my own newserver ( tweaknews ) and when I enter the details sabnzb accepts it, but placed the server as number three, wich means that Sabnzb always looks first to server 1 and 2. I have tried to deleted these servers but the system doesn't like that. Is there a way to delete these two servers because I only want to use my own newsserver ? ( I have noticed on page two on thes form that other users also had the same problem but there was not a solution told really to solve the problem. Can somebody help me, because this is the only program that I need and running and the I can trow windows really out of the window and work with Ubuntu :biggrin:

Many thanks

Straydog50

---

### Post by Martje_001 on 2007-09-01
You can manually edit the config file by typing:
```
gedit ~/.SABnzbd/sabnzb/SABnzbd.ini
```
in a terminal.

---

### Post by straydog50 on 2007-09-02
> **Martje_001 said:**
> You can manually edit the config file by typing:
```
gedit ~/.SABnzbd/sabnzb/SABnzbd.ini
```
in a terminal.

Thanks for the reply, but when i do this, the ini file is open in the text editor, but It's totally blank. am I diong something wrong or not ? I still can deleted the newsservers and replace them for miine. anyone got a clue why it&#347; not working ?

thanks for all your help and answers

Straydog50

---

### Post by Martje_001 on 2007-09-02
search for the file 'sabnzbd.ini' on you're computer (locations --> search). I think I've given the wrong filepath.

---

### Post by newportl on 2007-09-10
Worked well for me, thanks. The only thing I had to do was edit the config file manually.

---

### Post by cchester on 2007-10-07
Hey I ran your installer but I type sabnzbd and it says command not found. Any ideas.

Thanks for any help on this. I just need a gui for my hellanzb that works and I will be golden in linux.

Thanks for the program too.

---

### Post by reblocke on 2007-10-09
> **cchester said:**
> Hey I ran your installer but I type sabnzbd and it says command not found. Any ideas.

Thanks for any help on this. I just need a gui for my hellanzb that works and I will be golden in linux.

Thanks for the program too.

Try
```
 ~/.SABnzbd/sabnzbd/SABnzbd.py -f ~/.SABnzbd/sabnzbd/SABnzbd.ini
```

---

### Post by cchester on 2007-10-10
Hi Thanks for the reply.

I did " ~/.SABnzbd/sabnzbd/SABnzbd.py -f ~/.SABnzbd/sabnzbd/SABnzbd.ini " and I got the following error " Traceback (most recent call last):
  File "/home/chris/.SABnzbd/sabnzbd/SABnzbd.py", line 37, in ?
    import cherrypy
ImportError: No module named cherrypy "

Was the installer supposed to install I guess cherrypy?

What should I try next?

Thanks for any help.

---

### Post by frolle on 2007-11-05
Has anyone got this working under 7.10?

---

### Post by mangurt on 2007-11-05
Hi all,
Trying to get sabnzbd to work on my system, and when I type sabnzbd in terminal, I get this error

/usr/share/themes/Peace/gtk-2.0/gtkrc:55: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:56: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/usr/share/themes/Peace/gtk-2.0/gtkrc:57: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.


Any clues?
Thanks

---

### Post by mptpro on 2007-11-08
Thanks for this great program - one of the reasons my switch from WIn is moving along faster than expected!

A few questions:
-It seems as though it doesn't DL the .par files (except one), is there way way to "force" it do DL all of them?
-When configuring the file via web localhost, it seems to take a long time to move between options and save the settings, like over 1 minute.
-Is there a way to update/refresh the screen at predetrmined intervals to see the progress?
-Is there a way to "force" the scanning of the "nzb" folder, or does it only do this at startup?
-Entering the ID # from Newzbin sometimres works, sometimes doesn't...

thanks!

---

### Post by poverpa1 on 2007-11-10
Hi,

I am very new to ubuntu and I was trying to install Sabnzbd with the file found here.
Everything seems to go well. When I start sabnzbd in the webbrowser I can see the correct page enz. But when I want to add a NZB file in. I get the following error:
 
[B]500 Internal error
The server encountered an unexpected condition which prevented it from fulfilling the request[/B]. 

In my sabnzbd logs I cant find any error, only in the cherrypy.log I have found an error: 

File "/home/user/.SABnzbd/sabnzbd/sabnzbd/__init__.py", line 682, in add_nzbfile
 NZBQ.add(NzbObject(filename, repair, unpack, delete, nzbfile.value))
  File "/home/user/.SABnzbd/sabnzbd/sabnzbd/nzbstuff.py", line 380, in __init__
    self.__avg_date = datetime.datetime.fromtimestamp(avg_age / valids)
**ZeroDivisionError: integer division or modulo by zero**

Anybody Ideas what has gone wrong here? I have searched for hours on google but unfortunately no results. 

Thnx in advance.

Grtz Paul

---

### Post by mptpro on 2007-11-17
Great program!

I've been running it for over a week with no problems... then, this morning there was a 404error when doing localhost in my browser.

Turns out, it was uninstalled?!?!?

No idesa how.  Somehow while it was running something uninstalled sabnzbd.

ubuntu 7.1

any idea?

---

### Post by backupdevice on 2007-11-19
> **poverpa1 said:**
> Hi,

I am very new to ubuntu and I was trying to install Sabnzbd with the file found here.
Everything seems to go well. When I start sabnzbd in the webbrowser I can see the correct page enz. But when I want to add a NZB file in. I get the following error:
 
[B]500 Internal error
The server encountered an unexpected condition which prevented it from fulfilling the request[/B]. 

In my sabnzbd logs I cant find any error, only in the cherrypy.log I have found an error: 

File "/home/user/.SABnzbd/sabnzbd/sabnzbd/__init__.py", line 682, in add_nzbfile
 NZBQ.add(NzbObject(filename, repair, unpack, delete, nzbfile.value))
  File "/home/user/.SABnzbd/sabnzbd/sabnzbd/nzbstuff.py", line 380, in __init__
    self.__avg_date = datetime.datetime.fromtimestamp(avg_age / valids)
**ZeroDivisionError: integer division or modulo by zero**

Anybody Ideas what has gone wrong here? I have searched for hours on google but unfortunately no results. 

Thnx in advance.

Grtz Paul

i've got the same problem. 

Also when i download a nzb file inthe designated folder, it dissapers  but there's no downloading. 

Need help with this

---

### Post by backupdevice on 2007-11-19
> **backupdevice said:**
> i've got the same problem. 

Also when i download a nzb file inthe designated folder, it dissapers  but there's no downloading. 

Need help with this

fixed it. You need to type SUDO sabznbd

---

### Post by mptpro on 2007-11-24
bump.

still having problems with the below issues....

-It seems as though it doesn't DL the .par files (except one), is there way way to "force" it do DL all of them?
-When configuring the file via web localhost, it seems to take a long time to move between options and save the settings, like over 1 minute.
-Is there a way to update/refresh the screen at predetrmined intervals to see the progress?
-Is there a way to "force" the scanning of the "nzb" folder, or does it only do this at startup?

---

### Post by mptpro on 2007-11-25
another strange problem having to do with permissions...

It seems that all files downloaded and processed via sabnzbd have the owner of "blank", and NOT me.

I can access the files but I cannot delete or rename them.  I have to use sudo to change ther permissions back to me, then I can delete or rename them.

Even if I change the permission of the foler first, then when sabnzbd places a new file in that folder, it once again has the owner that is not me.

any ideas?

---

### Post by backupdevice on 2007-11-25
> **mptpro said:**
> another strange problem having to do with permissions...

It seems that all files downloaded and processed via sabnzbd have the owner of "blank", and NOT me.

I can access the files but I cannot delete or rename them.  I have to use sudo to change ther permissions back to me, then I can delete or rename them.

Even if I change the permission of the foler first, then when sabnzbd places a new file in that folder, it once again has the owner that is not me.

any ideas?

can not help you on he specific problem, but i was wrestling till yesterday with sabnzb, i gave it up. 

I installed hellanzb, took some while to read the cmplete howto and editting the config, but it works like a charm .

I recomend it to you

---

### Post by nikopol on 2007-11-29
It looks like SABnzbd has stopped being updated and there's a forking of the code to sabnzbdplus on sourceforge). There's a huge problem with Cherrypy v. 3  as sabnzb only seems to work with v. 2. Maybe a downgrade will solve it?

---

### Post by punking on 2007-12-23
I've just installed SABnzbd (and my first day from XP to Ubuntu, so a lot of learning to do). I have everything set up but it's not downloading the nzb. Here's a segment from my log

2007-12-23 12:37:26,394::INFO::_yenc module... found!
2007-12-23 12:37:26,394::INFO::celementtree module... NOT found!
2007-12-23 12:37:26,395::INFO::par2 binary... found!
2007-12-23 12:37:26,395::INFO::rar binary... found!
2007-12-23 12:37:26,395::INFO::unzip binary... found!
2007-12-23 12:37:26,397::INFO::Starting SABnzbd v0.2.5
2007-12-23 12:37:26,398::DEBUG::[sabnzbd] Starting postprocessor
2007-12-23 12:37:26,398::DEBUG::[sabnzbd] Starting assembler
2007-12-23 12:37:26,398::DEBUG::[sabnzbd] Starting downloader
2007-12-23 12:37:26,424::DEBUG::[sabnzbd] Starting dirscanner
2007-12-23 12:37:26,424::INFO::Starting web-interface
2007-12-23 12:37:26,430::INFO::[sabnzbd.misc] Dirscanner starting up
2007-12-23 12:37:26,430::DEBUG::[trylist] Appending secure.usenetserver.com:443 to <NzbFile: filename=video.nzb, type=None>.__try_list
2007-12-23 12:37:26,431::DEBUG::[trylist] Appending secure.usenetserver.com:443 to <NzbObject: filename=1198369690.nzb>.__try_list
2007-12-23 12:37:26,431::DEBUG::[trylist] Appending news.usenetserver.com:119 to <NzbFile: filename=video.nzb, type=None>.__try_list
2007-12-23 12:37:26,432::DEBUG::[trylist] Appending news.usenetserver.com:119 to <NzbObject: filename=1198369690.nzb>.__try_list
2007-12-23 12:37:54,661::INFO::[downloader] Resuming

I set it up so server 0 would be ssl and server 1 just normal because I didn't know if SABnzbd handles ssl.

Any thoughts appreciated. Thanks.

---

### Post by samoid on 2007-12-25
Hi, i was trying to install Sabnzbd using this [http://terminalnerd.blogspot.com/200...ntu-gutsy.html](http://terminalnerd.blogspot.com/200...ntu-gutsy.html)
i got up to the final configuration and when i put mv SABnzbd.ini.sample ~/.sajavascript:void(0)bnzbd.ini into the terminal i get bash: syntax error near unexpected token `('

thanks ahead of time for your help

---

### Post by synapse007 on 2008-02-22
Can someone please write a short tutorial on how to get sabnzbd to auto start without login ? Thanks in advance.

---

### Post by Martje_001 on 2008-02-24
Hello Synapse007,
This is a bit tricky. Please read this carefully (Make sure you have version 0.3.0 or higher installed!)

First: fire up a terminal (ALT+F2 --> gnome-terminal). Type:
```
sudo cp /usr/bin/sabnzbd /etc/init.d/sabnzbd
```
[I]
[SIZE="1"](If you want to run the program as not root (this may be useful, because you will not need root privileges to delete your downloaded files), you have to edit the file:
```
sudo nano /etc/init.d/sabnzbd
```
Put 'su yourusername' in the second line (below #!/bin/bash) and put '-f /home/USERNAME/.sabnzbd/sabnzbd.ini' after the third. Save it with CTRL+O and exit with CTRL+X.)[/SIZE][/I]

Now we have to edit the file (maby again? ;) )
```
sudo nano /etc/init.d/sabnzbd
```
after *python /usr/share/SABnzbd/SABnzbd.py* put *--browser 0 -d*. The file looks like this now:
```
#!/bin/bash
python /usr/share/SABnzbd/SABnzbd.py --browser 0 -d

```

Now we have to do 3 more steps:
```
sudo chmod +x /etc/init.d/sabnzbd
sudo update-rc.d -f sabnzbd remove
sudo update-rc.d -f sabnzbd defaults

```

Like I said. This is a bit tricky, but I hope I made it clear now. Cheers!

Martje_001

---

### Post by w.d on 2008-03-13
I just found out there's a 0.3.3 version. How can I update my existing SABnzbd 0.3? Is it possible that I manually alter your script and that it overwrites the older SABnzbd files, or do I have to remove the old ones manually and then install the new SABnzbd?
Thanks!

---

### Post by Martje_001 on 2008-03-13
I've updated the script. Please run it again, ether by using the [grapical instructions]("http://www.xs4all.nl/~mgj1/SABnzbd%20for%20linux/") or the terminal ones:
```
wget http://www.xs4all.nl/%7Emgj1/SABnzbd%20for%20linux/SABnzbd.sh
chmod +x SABnbzd.sh
./SABnzbd.sh
rm SABnzbd.sh
```
This will remove your old SABnzbd (but not your settings) and install 0.3.3.

---

### Post by w.d on 2008-03-14
Martje, thanx very much!!:) Martje bedankt!

---

### Post by Martje_001 on 2008-03-14
Graag gedaan hoor ;)

---

### Post by ariek on 2008-03-17
Hi,

Is there a way run this script on ubuntu server? I know it needs some adaptation, but it would be great to run SABnzbd on a simple server instance.

Just to let you know, there's also an other web based usenet download manager URD [http://ubuntuforums.org/showthread.php?t=718826&highlight=urd](http://ubuntuforums.org/showthread.php?t=718826&highlight=urd).

---

### Post by Martje_001 on 2008-03-17
Yes, I've made a script for servers. Please run this:
```
wget http://www.xs4all.nl/%7Emgj1/SABnzbd%20for%20linux/SABnzbd-server.sh
chmod +x SABnzbd-server.sh
./SABnzbd-server.sh
```

And [this](http://ubuntuforums.org/showpost.php?p=4395298&postcount=62) to make it run at startup.

---

### Post by ariek on 2008-03-17
Martje,

Wederom bedankt;-)

Does this also allow me to connect to the server with a web browser connection? (Like [http://SERVERNAME](http://SERVERNAME) or IP-ADDRESS:8080)

---

### Post by Martje_001 on 2008-03-17
> **ariek said:**
> Martje,

Wederom bedankt;-)
En weer graag gedaan ;P

btw: I didn't knew about URD, thanks, I'm going to check it out!

---

### Post by ariek on 2008-03-17
Does this also allow me to connect to the server with a web browser connection? (Like [http://SERVERNAME](http://SERVERNAME) or IP-ADDRESS:8080)[/quote]

---

### Post by Martje_001 on 2008-03-17
Yes,

[http://localhost:8080/sabnzbd](http://localhost:8080/sabnzbd)

---

### Post by ariek on 2008-03-17
> **Martje_001 said:**
> Yes,

[http://localhost:8080/sabnzbd](http://localhost:8080/sabnzbd)


This doesn't work from another machine, which I have just tested.

---

### Post by Martje_001 on 2008-03-17
Yes, that's something with the server settings (not the one from the web-interface!). You might, want to [install SABnzbd 0.2.5.]("http://ubuntuforums.org/showthread.php?t=320475&highlight=jtt1560") which does not have any security restrictions.

---

### Post by ariek on 2008-03-17
After searching the SABnzbd+ forum, there seems to be an easy solution. In the /home/USERNAME/.sabnzbd/.sabnzbd.ini there are luckily many settings to be changed.
To make the SABnzbd+ application accessible from any host, change the setting
> host = localhostto
 > host = 0.0.0.0

---

### Post by Martje_001 on 2008-03-17
OK! Thank you. I will add it to the first post.

---

### Post by ariek on 2008-03-19
> **Martje_001 said:**
> Yes, I've made a script for servers. Please run this:
```
wget http://www.xs4all.nl/%7Emgj1/SABnzbd%20for%20linux/SABnzbd-server.sh
chmod +x SABnzbd-server.sh
./SABnzbd-server.sh
```And [this]("http://ubuntuforums.org/showpost.php?p=4395298&postcount=62") to make it run at startup.


Hi Martje,

Thanks for the effort you took to create a SABnzbd installation script for Ubuntu server. The script runs great, but I think you need to put the "apt-get install..." as one of the first commands, because unzip is used before it is installed.

Now you first need to startup SABnzbd manually as a user (from your shell) with the command
```
sabnzbd
```The files needed for the application, will be installed automatically to the .sabnzbd in the user's home directory.
```
/home/USERNAME/.sabnzbd
```

Also if you want to use startup SABnzbd automatically, only works if you let the SABnzbd.py script know where the ini file is. So:
```
python /usr/share/SABnzbd/SABnzbd.py -f /home/USERNAME/.sabnzbd/sabnzbd.ini --browser 0 -d
```
Just out of curiosity, have you tried to get this running with Apache as well? 

How did you get along with URD?

---

### Post by Martje_001 on 2008-03-19
> **ariek said:**
> Also if you want to use startup SABnzbd automatically, only works if you let the SABnzbd.py script know where the ini file is. So:
```
python /usr/share/SABnzbd/SABnzbd.py -f /home/USERNAME/.sabnzbd/sabnzbd.ini --browser 0 -d
```
Yes, I knew that, but forget to mention it, thank you for saying.
> Just out of curiosity, have you tried to get this running with Apache as well? 
No, I didn't, because Apache eats a lot more resources (except if you're already running it, of course). I will look at it!
> How did you get along with URD? 
I haven't tried it yet. I'm very busy with school at the moment (~3 tests a day ;)). I will try it when I've made all my tests.

---

### Post by jipke on 2008-03-24
I've succesfully installed sabnzbd using your script. Thanks!

I've got two (noobish) questions.

- When I close FF sabnzbd seems to keep on downloading. Is there any way to stop it using the terminal?

- I've noticed (looking at conky) that there is also outbound traffic (+/- 10kb/s) when using this program. Is this normal? This isn't a p2p program, right? So, there should only be inbound traffic. 

Anyone who can explain this? Thanks in advance!

---

### Post by Martje_001 on 2008-03-24
First of all, I want to say thank you to you for using my script.
> **jipke said:**
> - When I close FF sabnzbd seems to keep on downloading. Is there any way to stop it using the terminal?
Yes, there is.
```
wget http://localhost:8080/sabnzbd/pause && rm index.html
```
or if you want to shut sabnzbd down:
```
wget http://localhost:8080/sabnzbd/shutdown && rm index.html
```

> **jipke said:**
> - I've noticed (looking at conky) that there is also outbound traffic (+/- 10kb/s) when using this program. Is this normal? This isn't a p2p program, right? So, there should only be inbound traffic.
No, there must be outbound traffic, because sabnzbd has to 'ask' the server if it may download the article. But, you're right, it isn't a P2P program, so nothing gets uploaded (no data).

---

### Post by Non Plus Ultra on 2008-05-03
is it just me or is the script removed from your webspace?

---

### Post by Martje_001 on 2008-05-03
> **Non Plus Ultra said:**
> is it just me or is the script removed from your webspace?
Yes and no ;). Yes from that place, here is the new one:
[http://www.xs4all.nl/~mgj1/sabnzbd.htm](http://www.xs4all.nl/~mgj1/sabnzbd.htm)

---

### Post by Noread on 2008-07-06
I got sabnzbd working on my server.

I want to make sabnzbd accessible from outside my LAN so I can check up on my downloads even when I'm not home. I forwarded port 8080 to the server but nobody can connect to the sabnzbd page.

I tried changing the host in the sabnzbd.ini file from 0.0.0.0 to the internal ip of the server, that didn't work, then I tried changing it to my external ip and my no-ip link, both of those gave an error when I tried to start sabnzbd.

I don't know what I need to change to make it work, can anybody help me?

---

### Post by Martje_001 on 2008-07-07
In sabnzbd.ini try both
```
0.0.0.0
```
and
```
0.0.0.0.
```
It may help. Good luck!

---

### Post by Noread on 2008-07-07
I got it working on a different port, seems like my isp blocks port 8080.

Is there any way to get sabnzbd and apache on port 80?

---

### Post by K.Mandla on 2008-07-07
Moved to General Help.

---

### Post by Martje_001 on 2008-07-07
> **Noread said:**
> I got it working on a different port, seems like my isp blocks port 8080.

Is there any way to get sabnzbd and apache on port 80?
You have to fill in (in sabnzbd.ini) port 80 and then run sabnzbd as root. Anything <1000 needs root priveliges in Linux.

---

### Post by Noread on 2008-07-07
> **Martje_001 said:**
> You have to fill in (in sabnzbd.ini) port 80 and then run sabnzbd as root. Anything <1000 needs root priveliges in Linux.

That doesn't work because apache uses port 80, I get an error saying port 80 is already in use. I want them to play together and get both of them using port 80.

---

### Post by nikopol on 2008-07-19
I'd getting a MD5 mismatch using the unstable repo. Anyone else getting that?

Thanks for your work Martje - btw any chance of an update to the latest stable? :)

---

### Post by ariek on 2008-07-19
For all those people who want an easy to install and complete usenet web client, try URD. It has just been updated, and is full of great features: [http://urdland.com](http://urdland.com)

---

### Post by Martje_001 on 2008-07-19
> **nikopol said:**
> I'd getting a MD5 mismatch using the unstable repo. Anyone else getting that?

Thanks for your work Martje - btw any chance of an update to the latest stable? :)
I'm creating a new site, so I don't have time to update the pages. Here you'll find the newest version:

[http://www.xs4all.nl/~mgj1/downloads/](http://www.xs4all.nl/~mgj1/downloads/)

I will update the repo's asap.

---

### Post by nikopol on 2008-07-19
Nice one Martje. Many thanks for the link.

Will take a look at URD ariek - always useful having another client as a backup.

---

### Post by h0ju on 2008-08-06
In apache try a proxy redirect in your virtualhosts. I would recommend using SSL w/ redirect and hiding your cherrypy from the outside world. Google will produce tons of tutorials on doing this.

---

### Post by kd7swh on 2008-11-08
Martje, Any chance of a 0.4.5 build being posted soon? I could easily build it myself but my laziness is prevailing.

---

### Post by Martje_001 on 2008-11-09
Yup. See [here](http://mbastiaan.nl/sabnzbd.php).

---

### Post by ikkedus on 2008-12-16
SABnzbd+ 0.4.6 .deb package is now available!

[**http://www.mbastiaan.nl/sabnzbd.php**]("http://www.mbastiaan.nl/sabnzbd.php")

;)

---

### Post by Martje_001 on 2008-12-16
Leipe gast? :popcorn:

Thx for reporting anyway!

---

### Post by ikkedus on 2008-12-17
@Martje_001

Yes, it's me ;-)

---

### Post by seethru on 2008-12-31
SABnzbd doesn't appear to start without logging in, and even then I need to ssh into my server and manually run sudo /etc/init.d/sabnzbd start. Any ideas? Also, I'm running trunk, but I've placed the files in the same place as your script is looking for them.

---

### Post by Martje_001 on 2009-01-01
Did you do the following?
```
chmod +x /etc/init.d/sabnzbd
sudo update-rc.d -f sabnzbd defaults

```

---

### Post by ikkedus on 2009-03-02
SABnzbd+ 0.4.7 .deb package for Ubuntu available!

Go to: [http://www.mbastiaan.nl/sabnzbd.php](http://www.mbastiaan.nl/sabnzbd.php)

:D

---

### Post by Revelation60 on 2009-03-05
I ran into some problems with the script, because it wasn't able to shutdown sabnzbd. After a pretty long search I found out it was my python version (2.6) that caused the problems. If you are experiencing the same issue, try this:

> 
#! /bin/bash

## CONFIG ##
USERNAME="yourname"
HOST="localhost"
PORT="8080"
## / CONFIG ##

case "$1" in
start)
        echo "Starting SABnzbd."
        sudo -u $USERNAME -H python2.5 /usr/share/sabnzbd/SABnzbd.py -f /home/$USERNAME/.sabnzbd/sabnzbd.ini --browser 0 -d
        ;;
stop)
        echo "Shutting down SABnzbd."
        wget -q -O /dev/null  http://$HOST:$PORT/sabnzbd/shutdown
        ;;
*)
        echo "Usage: $0 {start|stop}"
        exit 1
esac

exit 0


Note the python2.5!

---

### Post by Martje_001 on 2009-04-02
0.4.8 available!

**SABnzbd is in Jaunty now!**

---

### Post by new_tolinux on 2009-04-23
Can someone help me please?
Sabnzbd does not seem to do anything at all, except loading, but no web interface at all.

I used the 0.4.9 package from [http://www.mbastiaan.nl/sabnzbd.php](http://www.mbastiaan.nl/sabnzbd.php) and also the sh-script.
Before that I tried the package which is availiable from within Kubuntu, and removed it before I tried the .deb from [http://www.mbastiaan.nl/sabnzbd.php](http://www.mbastiaan.nl/sabnzbd.php) because that did not work either.

Everytime I keep getting an error when I try to load [http://localhost:8080/sabnzbd](http://localhost:8080/sabnzbd)
Don't know the real English translation, sorry.
In Dutch Konqueror keeps saying:
De gevraagde handeling kon niet worden voltooid
Verbinding met de server geweigerd

~/.sabnzbd/logs/cherrypy.log reads:
HTTP INFO Serving HTTP on [http://localhost:8080/](http://localhost:8080/)
which seems OK to me

~/.sabnzbd/logs/sabnzbd.log reads no errors

Edit:
For now the problem is solved.
Replaced Kubuntu Jaunty with Ubuntu Jaunty and everything is working perfectly :)
Thanks for the help ;)

---

### Post by shadowlands on 2009-05-26
I installed from the home page for SABnzbd.  So will I need to put my user name in or is all of hat taken care of? I will still need a newsreader and a news client correct or am I incorrect in my thinking?

---

### Post by libertao on 2009-09-29
So is this no longer being hosted? :(

edit: nevermind I see there are pretty easy terminal instructions on sabnzbd homepage now. :)

---

### Post by swholst on 2011-04-25
sabnzbdplus seems to be giving me issues :(. How do I completely remove it so that I can start fresh?

---

