---
title: "Howto: Install Domino 8.0.1 on Ubuntu"
date: 2008-02-26
forum: General Help
---

### Post by SpaceTeddy on 2008-02-26
[UPDATE]
20.04.2008 - I've just tested this Configuration on a Ubuntu 8.04 Server. These Steps apply for 8.04 aswell.
[/Update]


Ok, i have been banging my Head against the wall for the past two weeks, but eventually i got it to work. And my mistake was so simple... now that i think of it

So others do not get hung up on mistakes i did, i will briefly explain how i got the domino 8.0.1 server (Package C18XSEN) working on an ubuntu 7.10 Server. 

[SIZE="5"]Get the System ready [/SIZE]
Install the Ubuntu Server in minimal mode (no extra packages) until you have booted into the system the first time.
The only package you have to install to get the server working is gawk. Do this via
> sudo apt-get install gawk
Next is that you need to create a user the Domino server should run under. I used the default one (notes). create the user via 
> sudo useradd -m notes
then check if the user really exists with
> id notes
this should give you something like
> # id notes
uid=1001(notes) gid=1001(notes) groups=1001(notes)

The next step is to copy the file (C18XSEN.tar) with the Domino server in it over to the server and unpack it
> tar -xf C18XSEN.tar

[SIZE="5"]Installation of Domino[/SIZE]
start the installation from the linux/domino subfolder with the install script
> cd linux/domino
./install -console
The -console tells it to run in textmode and not try to find a xserver

The install is pretty straight forward, i took the default for everything BUT the setup (switched that to remote setup) and everything worked quite nicely. Remember that this will ask you for the user the Domino server runs under. If you used something else than notes, please adjust the setup accordingly.

When the install is done, domino will ask you if you want to launch the remote server setup right away. Answer this one with yes.

[SIZE="5"]Remote setup[/SIZE]
For this step, you need a windows that has the Domino Administrator installed. With that one, select "remote server setup" and connect to the fresh install. Everything should work fine, and in the end tell it to stop the server aswell.

[SIZE="5"]Manageing the Enviroment[/SIZE]
In my installation, domino was not able to handle the UTF-8 coding of the language. So whenever i started it, it gave me cryptic numbers instead of messages. to fix this, go into the folder /opt/ibm/lotus/notes/latest/linux/res. once there, there should be a folder called en_EN.UTF-8 or de_DE.UTF-8. create a softlink in to this folder without the .UTF-8 bit append to it with this command (if your locale is english)
> cd /opt/ibm/lotus/notes/latest/linux/res
sudo ln -s en_EN.UTF-8 en_EN

The next quirk is that the domino server is not able to find it's libraries. To fix that, you will need to set the environment variable LD_LIBRARY_PATH. Best way (for me) do to that is to add it to the /etc/environment file. So, add this line to the end of the file
> LD_LIBRARY_PATH="/opt/ibm/lotus/notes/latest/linux"

[SIZE="5"]starting the Domino Server[/SIZE]
i have not yet found/written a start script for the domino Server so i still do it manually. Log in as the user notes and change into the data directory of your notes server (for me it is /local/notesdata)
once there, you can start the server with /opt/ibm/lotus/bin/server. It should boot up nicely and run as long as that console is open. I usually start it in a screen session so that i can close the terminal and the server keeps running.
> cd /local/notesdata
/opt/ibm/lotus/bin/server
**NOTE:** Here was my big problem. I used to start the server with the command /opt/ibm/lotus/notes/latest/linux/server and it also boot up, but the HTTP process (webserver) of the Domino crashes with the error "Unable to find VM - Aborting". Why that is the case, i don't know, but somehow this way of starting it works

[SIZE="5"]we are done[/SIZE]
that should have been it. The server is running smoothly and you can use your Client/Administrator to start configuring it. 

Hope this helps people like me who get stuck on stupid errors nobody can explain :(

---

### Post by SpaceTeddy on 2008-02-29
[SIZE="5"]Start/Stop Script for Domino 8.0.1 on Ubuntu Server 7.10[/SIZE]

I found an old start script for a domino server on a debian etch install running notes 6.5. This script did not work with the ubuntu 7.10 server, so i heavily modified it to work again. I don't know yet if it fully works, but as far as i could test it, it did to the job.. more or less :)

The files are attached. if you want to use it, do the following
 * copy the file **domino** into the folder /etc/init.d
 * copy the file **lotusdomino** into the folder /etc/default
 * make both files executable
 * change owner on both files to be root
 * add a softlink to gawk in /usr

once that is done, the script should work (or so it did for me)

PS: i used this way, because the script offered [here]("http://www.nashcom.de/nshweb/pages/startscript.htm") for domino server does not seem to work on ubuntu... or i am too silly to get it to work

---

### Post by jpmd on 2008-03-14
Thanks for the great tips.  It helped me get Domino installed.

The amazing thing is that I've got a 10 year old P2-450 MHz computer with 256 MB of RAM, yet Ubuntu steams right along, even with Samba, Lighttpd (web server) and Domino (web/Notes server) all running at the same time!  What a welcome change from my previous (Redmond) environment!

I couldn't get the automatic thing to work (haven't figured out the whole services thing yet -- I'm an Ubuntunewbie) but since my environment is strictly for testing and training (I recently taught a university class in "Rapid App Dev with IBM Lotus Notes"), I'm not too worried.

However, I did struggle to figure out how to start the Domino server remotely from a Putty window, and without having to keep that window open.  (I can't remember where I found this tip, unfortunately.)

Anyway, if I enter this as one line in the remote window, Domino will start and continue to run, while still returning control of the window to me for other server stuff.  I believe it's the final '&' that makes that work.

[FONT="Courier New"]cd /local/notesdata && /opt/ibm/lotus/bin/server &[/FONT]

Dang, this is cool stuff!

---

### Post by SpaceTeddy on 2008-03-14
there are acctually quite a number of way to start it. The thing is, i like to have to start automaticially on boot, so i do not have to worry about loging into the server if it reboots and start it manually. 

Also, when you do it like that, you do not get the messages that are printed to the console. Of course, these are usually also found in the log.nsf (or something like that), but sometimes it is just handy having them in a textfile where you can grep quickly.

so, i would suggest to alter that command into
> cd /local/notesdata && /opt/ibm/lotus/bin/server &> /var/log/domino
to make sure that the logs are acctually being written properly.

The other alternative is to start domino in a screen session. This way, you can always reattach yourself to the session - even if you close your ssh session or the conection breaks - screen stays open ! :)

nice to know that this howto acctually helped someone :)

---

### Post by Top-Gear on 2008-05-21
I have followed your instructions but Domino C18XSEN fails to install for me.  The ./install script tells me it is loading Java VM then drops back to the command line.  Could you please explain which packages you have installed as I feel I must be missing something important.  Have you set any other parameters to convince this installation script to behave itself?  

This is my first experience with Ubuntu and I am hoping to have a minimal system to run Domino as cleanly as possible so I have only loaded the base Ubuntu 8.04 so far.

---

### Post by SpaceTeddy on 2008-05-21
let me think what i did... back when i installed the thing... 
I know i had that problem with the crashing installer too, but i cannot remember how i fixed it... 

have you started the installer as root ? i don't mean sudo ./install, i mean typing sudo su and becoming root all together ?

about the only thing i can possibly think of... really

---

### Post by Top-Gear on 2008-05-22
Thanks for the response.

Yes I have tried running as root.  Sudo -i

Did you set the linux type anywhere?  Looks like the script triggers off that somehow.

I forgot to mention that I am running the 64 bit version of Ubuntu - hopefully not an issue.  Have you any experience with 64 bit Domino?

---

### Post by SpaceTeddy on 2008-05-22
and here we have the problem. 64-bit !
Domino is a precompiled set of binaries for a 32-bit system. I've tried running it on a 64-bit system myself - no chance to get it working. I've also checked the IBM download sides if i can find a 64 bit version - they do not supply one. 

You *must* use a 32-bit version of ubuntu if you want to run a domino server on it... only way i got it to work.

sorry to bring the bad new. If i ever stumple upon a 64-bit version i will try it and update this howto. So far, i have not found one :(

---

