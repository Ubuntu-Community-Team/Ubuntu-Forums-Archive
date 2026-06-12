---
title: "Dynamips"
date: 2007-04-26
forum: General Help
---

### Post by Rhodan on 2007-04-26
Hi,

I'm just wondering if there are any users of Ubuntu that have installed and used Dynamips successfully on Feisty ? Are there repositories for it ?

Thx

---

### Post by dreadlord_chris on 2007-04-26
> **Rhodan said:**
> Hi,

I'm just wondering if there are any users of Ubuntu that have installed and used Dynamips successfully on Feisty ? Are there repositories for it ?

Thx

Is this what you are talking about?
[http://packages.debian.org/unstable/net/dynamips](http://packages.debian.org/unstable/net/dynamips)

Haven't used it, but you can get it from there.

---

### Post by Rhodan on 2007-04-27
Yeah that's it, just wondering if anyone here is using it under Feisty ?

---

### Post by Gregzx on 2007-06-02
Did you manage to install it?

---

### Post by k84 on 2007-06-07
I got the executable from [this tutorial]("http://www.ipflow.utc.fr/index.php/Cisco_7200_Simulator")  , it runs well if you know how to set the parameters, I got an IOS image a bit older than the one in the tutorial... the bad thing is that my laptop overheats quick when I run the simulator, I don't know how that can be solved.

---

### Post by tonyperez on 2007-06-30
Hi K84 ...

You must to configure idlepc. I use Dynagen, that is a front end for Dynamips [www.dynagen.org](www.dynagen.org) try this.

---

### Post by windwalker78 on 2007-07-11
Hi all,

Glad to share I did it :guitar:. I got it working with bridging too . Dynamips&Dynagen just rock. I tested on feisty. I am far from expert, but would galdly help on this matter. 

Regards,
Todor

---

### Post by geezerone on 2008-01-14
Hi

I have followed [ this blindhog ](http://www.blindhog.net/tutorials/dynagen-linux-install.htm) guide and get dynamips to start but when trying dynagen simple1.net the message "could not open simple1.net" is shown?

Any ideas. I got dynamips/dynagen to work on Windows ok. If there is a better way and more straightforward way to install dynamips/dynagen please do tell.

Thanks

P.S. I didn't know how to stop iptables but don't know if this is the reason?

---

### Post by intelligentfool on 2008-01-29
what about GNS3? Some might call it a bit "girly" but i still like making a topo map and then hitting 'run' instead of having to refer to a spreadsheet with 10 routers on it. 

btw, speaking of which, any ideas as to how many routers a machine with 2ghz P4 and 2gb of ram can run in dynamips? my CCNP book has practice labs at the end of each chapter, but they all use about 6 or 7 routers... my laptop with 1.5ghz and 750mb of ram using XP can get a max of 4 routers, so i'm thinking my better equipped desktop running ubuntu 7.10 should be able to do at least double that.... i'll find out tonight though.

---

### Post by tonyperez on 2008-03-09
> **geezerone said:**
> Hi

I have followed [ this blindhog ](http://www.blindhog.net/tutorials/dynagen-linux-install.htm) guide and get dynamips to start but when trying dynagen simple1.net the message "could not open simple1.net" is shown?

Any ideas. I got dynamips/dynagen to work on Windows ok. If there is a better way and more straightforward way to install dynamips/dynagen please do tell.

Thanks

P.S. I didn't know how to stop iptables but don't know if this is the reason?

Hi geezerone ..

I think the problem is the path for the "image=" line on the net file. You must create a path where the IOS image bin file resides and give it privileges for read, write and excecution.

For example:

U could create a directory on opt whith the name images:

sudo mkdir /opt/images

Then copy or move ios bin file to that path (for this example i assume that the ios bin files exist on the default pathi for the user--in this case tony--):

cd /opt/images
sudo mv /home/tony/7200-AD.bin .

Then give it privileges to the user:

cd /opt
sudo chown -R root:tony images/
sudo chmod -R 775 images/

Now u can configure your net file with the right path:

[localhost]

    [[7200]]
    image = /opt/images/7200-AD.bin
    # On Linux / Unix use forward slashes:
    npe = npe-400
    ram = 160
        
    [[ROUTER R1]]
    s1/0 = R2 s1/0
    
    [[router R2]]
    # No need to specify an adapter here, it is taken care of
    # by the interface specification under Router R1tony@Kannon:/opt/dynagen-0.1

Try this and if u got a problem, please post the errors and net file.

Greetings !!! and sorry for my bad english.

---

### Post by geezerone on 2008-03-11
Thanks for the reply tonyperez!

I have to run both Dynamips and Dynagen as root (sudo -s) but should this be the case?

The chmod and chown I have seen before but any links appreciated!

Thanks again. :)

---

### Post by tonyperez on 2008-03-11
> **geezerone said:**
> Thanks for the reply tonyperez!

I have to run both Dynamips and Dynagen as root (sudo -s) but should this be the case?

The chmod and chown I have seen before but any links appreciated!

Thanks again. :)

geezerone ...

U could check this link,  [http://7200emu.hacki.at/viewtopic.php?t=5025](http://7200emu.hacki.at/viewtopic.php?t=5025) from the Hacki forum. U'll find a lot tips, tutorials, how to's and even net sample files.

btw ... i forgotto say  that the best way to run dynamips/dynagen is to create simlinks on /usr/local/bin to the bin files for dynamips and dinagen.

I really want to help u ... i allready install dynagen/dynamips without no problems.

Greetings !!

---

### Post by tonyperez on 2008-03-12
I already install dynamips/dynagen on Ubuntu 7.10 without problems with this procedure:

Create a directory named temp on your home path.
--- tony@Kannon:~$ mkdir temp

Download the  dynamips-0.2.8RC1-1.i386.rpm and  dynagen-0.10.1.tar.gz from the dynagen page and save them on temp.

Decompress the files using the file browser (do a rigth click and select Extract here). If u get an error extracting the rmp file install the librpm.

Go to the opt directory:
--- cd /opt

Move dynamips and dynagen directories to opt (change tony to your user):
--- sudo mv /home/tony/temp/dynagen-0.10.1 .
--- sudo mv /home/tony/temp/dynamips-0.2.8RC1-1 .

Go to /usr/local/bin and create simlinks to bin files:
--- cd /usr/local/bin
--- sudo ln -s /opt/dynagen-0.10.1/configspec
--- sudo ln -s /opt/dynagen-0.10.1/dynagen
--- sudo ln -s /opt/dynamips-0.2.8RC1-1/usr/bin/dynamips
--- sudo ln -s /opt/dynamips-0.2.8RC1-1/usr/bin/nvram_export

Go to /usr/local/etc and create simlink to dynagen.ini:
--- cd /usr/local/etc
---  sudo ln -s /opt/dynagen-0.10.1/dynagen.ini

Change the owner for the dynamips/dynagen directories (change tony to your user):
--- sudo chown -R root:tony dynamips-0.2.8RC1-1/
--- sudo chown -R root:tony dynagen-0.10.1/

Give them permissions  (change tony to your user):
--- sudo chmod -R 775 dynamips-0.2.8RC1-1/
--- sudo chmod -R 775 dynagen-0.10.1/

At this point u must to have someting like this on /opt, /usr/local/bin and /usr/local/etc:

tony@Kannon:/opt$ ls -l
drwxrwxr-x 6 root  tony   4096 2008-02-29 22:04 dynagen-0.10.1
drwxrwxrwx 4 root  tony   4096 2008-02-12 00:18 dynamips-0.2.8RC1-1

tony@Kannon:/usr/local/bin$ ls -l
total 0
lrwxrwxrwx 1 root root 30 2008-02-29 21:55 configspec -> /opt/dynagen-0.10.1/configspec
lrwxrwxrwx 1 root root 27 2008-02-29 21:55 dynagen -> /opt/dynagen-0.10.1/dynagen
lrwxrwxrwx 1 root root 41 2008-02-29 21:56 dynamips -> /opt/dynamips-0.2.8RC1-1/usr/bin/dynamips
lrwxrwxrwx 1 root root 45 2008-02-29 21:56 nvram_export -> /opt/dynamips-0.2.8RC1-1/usr/bin/nvram_export

tony@Kannon:/usr/local/etc$ ls -l
lrwxrwxrwx  1 root root   31 2008-02-29 21:55 dynagen.ini -> /opt/dynagen-0.10.1/dynagen.ini


At this point u must be able to run dynamips but, surely u will get and error telling u that dynamips can't find the libpcap shared libraries.
tony@Kannon$ dynamips -H 7200 &
[1] 7378
tony@Kannon$ dynamips: error while loading shared libraries: libpcap.so.0.9.4: cannot open shared object file: No such file or directory

This can fix it creating a simlink to the libpcap that u have installed on your system:
--- cd /usr/lib
--- sudo ln -s libpcap.so.0.8  libpcap.so.0.9.4

tony@Kannon:/home/tony$ Cisco Router Simulation Platform (version 0.2.8-RC1-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: Sep 10 2007 21:54:52

Unable to create log file (Permission denied).

[1]+  Exit 1                  dynamips -H 7200

Ok, libpcap error were fixed. But now we have an error telling us that dynamips can't create the log file because we don't have write permisson. This happened because the default path for dynamips to create the log file is /var/log and we don't have permissons to that path.
Fix it creating a dynamips.log blank file on /opt/dynamips-0.2.8RC1-1 and give it permissons (change tony to your user):
--- cd /opt/dynamips-0.2.8RC1-1
--- gksudo gedit dynamips.log
--- save the file and close gedit
--- sudo chown root:tony dynamips.log
--- sudo chmod 775 dynamips.log

tony@Kannon:~$ dynamips -H 7200 -l /opt/dynamips-0.2.8RC1-1/dynamips.log &
[1] 7523
tony@Kannon:~$ Cisco Router Simulation Platform (version 0.2.8-RC1-x86)
Copyright (c) 2005-2007 Christophe Fillot.
Build date: Sep 10 2007 21:54:52

Log file: writing to /opt/dynamips-0.2.8RC1-1/dynamips.log
ILT: loaded table "mips64j" from cache.
ILT: loaded table "mips64e" from cache.
ILT: loaded table "ppc32j" from cache.
ILT: loaded table "ppc32e" from cache.
Hypervisor TCP control server started (port 7200).

tony@Kannon:~/Labs$

Bingo !!!!

There is a final step to have dynagen running. We must specify to dynagen where to find the configspect file, and for that, we have to edit the dynagen file:
--- DON'T FORGET TO MADE A BACKUP FIRST !!!!
--- cd /opt/dynagen-0.10.1
--- cp dynagen dynagen.bak
--- gksudo gedit dynagen
--- edit this lines:
#CONFIGSPECPATH = [ "/usr/share/dynagen", "/usr/local/share" ]
CONFIGSPECPATH = [ "/usr/local/bin" ]
--- save the file and close gedit

Now, what about the ios image files ??? ok ... we can live them on the user home path and create an IOS directory (just to give an example) and we don't have to give it permissons because we are the owner and have full privileges.

--- cd /home/tony
--- mkdir IOS
--- put image files here

Configure your net file to tell dynagen where to find images files:

# Simple lab

[localhost]

    [[7200]]
    # On Linux / Unix use forward slashes:
    image = /home/tony/IOS/C2691-AD.bin
    npe = npe-400
    ram = 160
        
    [[ROUTER R1]]
    s1/0 = R2 s1/0
    
    [[router R2]]
    # No need to specify an adapter here, it is taken care of
    # by the interface specification under Router R1

Run dynagen

--- dynagen test.net

Reading configuration file...

Shutdown in progress...
Shutdown completed.
rommon_load_file: unable to create file c2691_ro-b_rommon_vars (No such file or directory)
rommon_load_file: unable to create file c2691_ro-c_rommon_vars (No such file or directory)
rommon_load_file: unable to create file c2691_ro-d_rommon_vars (No such file or directory)
rommon_load_file: unable to create file c2691_ghost-C2691-IP-ENT.bin-localhost_rommon_vars (No such file or directory)
CPU0: carved JIT exec zone of 64 Mb into 2048 pages of 32 Kb.
NVRAM is empty, setting config register to 0x2142
C2691 instance 'ghost-C2691-IP-ENT.bin-localhost' (id 4):
  VM Status  : 0
  RAM size   : 128 Mb
  NVRAM size : 128 Kb
  IOS image  : /opt/dynagen-0.10.1/images/C2691-IP-ENT.bin

Loading ELF file '/opt/dynagen-0.10.1/images/C2691-IP-ENT.bin'...
ELF entry point: 0x80008000

C2691 'ghost-C2691-IP-ENT.bin-localhost': starting simulation (CPU0 PC=0xffffffffbfc00000), JIT enabled.

C2691 'ghost-C2691-IP-ENT.bin-localhost': stopping simulation.
Network successfully loaded

Dynagen management console for Dynamips
Copyright (c) 2005-2007 Greg Anuzelli

=>

Bingo !!!

---

### Post by geezerone on 2008-03-20
Thanks, will have a go and let you know how I get on!!

---

### Post by SmarterThanMyPhone on 2008-03-20
Im using it to test IOS configs with my ACS server right now, Im not the cisco guy, I just set it up, but he loves it.

---

### Post by geezerone on 2008-03-23
Hi

Just setup using various aspects of the procedure (from your hacki link) so thanks for that!!! 

Will have a bash (pardon the pun ;) ) and let you know how I get on!

Just a quick question, when exporting from dynagen window using the "export R1 savedconfigs" the configs are stored in my simple1 folder and not in any other I may want to stipulate. Is there a quick way (like in windows) of specifying a path (/home/username/Documents/savedconfigs/) for example??

Thanks

---

### Post by tonyperez on 2008-03-24
> **geezerone said:**
> Hi

Just setup using various aspects of the procedure (from your hacki link) so thanks for that!!! 

Will have a bash (pardon the pun ;) ) and let you know how I get on!

Just a quick question, when exporting from dynagen window using the "export R1 savedconfigs" the configs are stored in my simple1 folder and not in any other I may want to stipulate. Is there a quick way (like in windows) of specifying a path (/home/username/Documents/savedconfigs/) for example??

Thanks

Hi

Ummm... i'm not sure about that... but if create a simlink to the path and specify to dynagen the simlink, the file will be save on the path that u are looking for.

=> export
export {/all | router1 [router2] ...} "directory"
saves router configs individual files in "directory"
Enclose the directory in quotes if there are spaces in the filespec.

---

