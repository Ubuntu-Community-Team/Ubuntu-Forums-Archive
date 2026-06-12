---
title: "Shrew Soft VPN not in Software Center"
date: 2012-10-30
forum: General Help
---

### Post by MichaelEber on 2012-10-30
I had Shrew Soft VPN installed on my 12.04 build of Ubuntu.  This was great because our VPN configurations file is created with Shrew!  I upgraded to 12.10 and it removed my install of Shrew.

I then did some searching and I found an Ubuntu web page that showed that it should be in the Software Center for 12.10.  But it does not exist.

I went to the Shrew site but for Linux we appear to be treated as third world users as they provide no install files.  

Any suggestions on how to get this back so I can remote into work???

By the way....pulling down source code, doing my own build, and all that other crap is not a solution.

---

### Post by kanikilu on 2012-11-02
I've never heard of it until now, but the package name is called "ike", and you're right, it isn't in the Quantal repos. The launchpad page for it says something about it being unmaintained?

[https://launchpad.net/ubuntu/quantal/amd64/ike](https://launchpad.net/ubuntu/quantal/amd64/ike)

Short of reinstalling 12.04, maybe you could try manually downloading the ike, and ike-qtgui, if you need it, debs and installing them?

[http://archive.ubuntu.com/ubuntu/pool/universe/i/ike/](http://archive.ubuntu.com/ubuntu/pool/universe/i/ike/)

Actually, just out of curiosity, I downloaded the deb for ike from the above link and it installed without error on my 12.10 system (exact package was "ike_2.1.7+dfsg-1.1_amd64.deb").

Can't say for sure if it *works* since I don't have a server to connect to, but it does install and starts a daemon...

BTW, it may not be necessary, but compiling from source doesn't look particularly difficult for this application:

[http://blog.htbaa.com/news/getting-shrew-soft-vpn-client-ike-for-ubuntu-to-work](http://blog.htbaa.com/news/getting-shrew-soft-vpn-client-ike-for-ubuntu-to-work)

Good luck :)

---

### Post by esvcv on 2013-01-17
Hi there,

I'm stuck installing this too..  apparently I need a dependency called libqt3 or something.

But as far as I can tell Qt3 has been superceded by Qt4 (there's no Qt3 in archive.ubuntu.com, only Qt4), and despite there being a "Qt4 with Qt3 support" package available which I have tried, the Shrew compiler doesn't seem to like this at all.

I always just end up with 
```
-- Could NOT find Qt3 (missing:  QT_QT_LIBRARY QT_INCLUDE_DIR) 
CMake Error at CMakeLists.txt:423 (message):
  Unable to locate required package : QT

```

Can anyone help???

Thank you!

---

### Post by thejapslap on 2013-01-29
Here's how I was able to install the Shrew Soft client on Ubuntu 12.10

---------------------------------------------- 
**Install Shrew Soft VPN client on Ubuntu 12.10  **
Note: If you already have a working Shrew Soft VPN client, use the 'export' feature to export the configuration settings. This file can easily be imported when the new version is up and running.  [B]

*Step 1: download shrew soft package*[/B] 
Download the latest linux schrew soft vpn package here: [http://www.shrew.net/download/ike](http://www.shrew.net/download/ike)  

At the time of writing (01/29/2013) the file is: ike-2.2.0-rc-2.tgz  It's not the stable release but works fine as far as I can tell.  

***Step 2: untar package*** 
Untar this into a directory and navigate to the folder created called: ike  [B]

*Step 3: try to prepare for install*[/B] 
run this command: cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES  [B]

*Step 4: install dependencies*[/B] 
the initial cmake command failed for me the first two times because I needed to install these dependencies:  

libedit 
qt4  

sudo apt-get install libedit-dev 
sudo apt-get install libqt4-core libqt4-dev libqt4-gui  

[B]*Step 5: prepare for installation:*
[/B]Run this command again: 
cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES  [B]

*Step 6: install the application using this command*[/B] 
sudo checkinstall  

***Step 7: launch the shrew soft daemon*** sudo iked  [B]

*Step 8: launch the graphical interface*[/B] 
sudo qikea  [B]

*Step 9: use the import feature or set up a new connection*[/B]  [B]

*Step 10: done*[/B]

---

### Post by esvcv on 2013-02-01
Thank you so much !!

I hadn't even noticed the beta versions available for download so I had been trying the latest stable release.

Have just followed your instructions and with the exception of not being able to run 'sudo checkinstall' and using 'sudo make install' instead all it went perfectly and I'm not successfully VPN'd into the office !!

---

### Post by Aydos on 2013-02-01
I have almost given up all hope.

When I run the following command I get this error

 cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- Using install prefix /usr ...
-- Using etc install path /etc ...
-- Using bin install path /usr/bin ...
-- Using sbin install path /usr/sbin ...
-- Using lib install path /usr/lib ...
-- Using man install path /usr/local/man ...
CMake Error at CMakeLists.txt:265 (message):
  Unable to locate openssl crypto include files


Any ideas?

---

### Post by esvcv on 2013-02-02
Looks like you need to install OpenSSL, try this:

```
sudo apt-get install libssl-dev libssl0.9.7 
```

---

### Post by Aydos on 2013-02-02
I tried that and I got this

sudo apt-get install libssl-dev libssl10.9.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libssl10.9.7
E: Couldn't find any package by regex 'libssl10.9.7'

---

### Post by esvcv on 2013-02-02
Sorry that was my mistake, there shouldn't be a 1 in there, try:

```
sudo apt-get install libssl0.9.7
```

---

### Post by Aydos on 2013-02-02
Well I am still getting this even with the new command

sudo apt-get install libssl0.9.7
[sudo] password for -----: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libssl0.9.7
E: Couldn't find any package by regex 'libssl0.9.7'

---

### Post by esvcv on 2013-02-02
Ok, could you try the following instead:

```
sudo apt-get install opensll
```

---

### Post by Aydos on 2013-02-02
I believe I had tried the openssl on my own yesterday before posting. When I run the command I get the below.

sudo apt-get install openssl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

However, it did tell me I needed to run autoremove for some old files so I did that.

Then when I tried the other again I got the same response.

sudo apt-get install libssl0.9.7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libssl0.9.7
E: Couldn't find any package by regex 'libssl0.9.7'


I am not sure why I am having such issues or why there is not a PPA for this. Sorry for all the problems with it and  thanks for all of the help.

Anyone know of any similar software that will let me import .pcf or .vcf files in the same manner? I need to be able to VPN back into work. If I can get this worked out soon I am going to have to put Windows on here or maybe Fedora since I can just yum install ike to get it to work there.

I would like to stick with Ubuntu if I can get this working or a similar program.

---

### Post by esvcv on 2013-02-02
Have you tried running ```
cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
``` again, since installing libssl-dev ?  Maybe that has fixed it already ?

---

### Post by Calinou on 2013-02-02
```
sudo apt-get install libssl-dev libssl0.9.8 libssl1.0.0
```

This?

---

### Post by esvcv on 2013-02-02
No, I mean try installing ShrewVPN again now that you have successfully installed the libssl-dev library...

go into the IKE folder and run the original command to set it up:

cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES

---

### Post by Aydos on 2013-02-03
Ok I ran sudo apt-get install libssl-dev libssl0.9.8 libssl1.0.0 with out any error and it installed.

Then I tried to install Shrew Soft VPN again.

Ok now I am getting this

cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- Using install prefix /usr ...
-- Using etc install path /etc ...
-- Using bin install path /usr/bin ...
-- Using sbin install path /usr/sbin ...
-- Using lib install path /usr/lib ...
-- Using man install path /usr/local/man ...
-- Looking for include file pthread.h
-- Looking for include file pthread.h - found
-- Looking for pthread_create
-- Looking for pthread_create - not found.
-- Looking for pthread_create in pthreads
-- Looking for pthread_create in pthreads - not found
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE  
-- Using library -lpthread
-- Looking for pthread_mutex_timedlock in -lpthread
-- Looking for pthread_mutex_timedlock in -lpthread - found
CMake Error at CMakeLists.txt:347 (message):

---

### Post by esvcv on 2013-02-03
Is that the entire output ?  It looks like there should be a description of the error message after what you posted...

---

### Post by Aydos on 2013-02-03
> **esvcv said:**
> Is that the entire output ?  It looks like there should be a description of the error message after what you posted...

I apologize. I did not realize my copy was cut off.

The missing line is

  Unable to locate required binary : flex

---

### Post by esvcv on 2013-02-03
that's better :)

flex is one of the dependencies, along with bison.  since you don't already have flex the chances are you won't have bison either.  both should be available from apt though, so try:

```
sudo apt-get install flex bison
```

And then try installing Shrew again... fingers crossed !

---

### Post by Aydos on 2013-02-03
Ok I fixed the above problem with a 
sudo apt-get install flex

Then tried to install again and got a similar error about bison
sudo apt-get install bison

Then tried the install again and got

cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- Using install prefix /usr ...
-- Using etc install path /etc ...
-- Using bin install path /usr/bin ...
-- Using sbin install path /usr/sbin ...
-- Using lib install path /usr/lib ...
-- Using man install path /usr/local/man ...
-- Using library -lpthread
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Performing Test NATT_FOUND
-- Performing Test NATT_FOUND - Success
-- Enabled NAT Traversal support ...
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt4: /usr/bin/qmake (found version "4.8.3") 
-- Enabled Client QT GUI support ...
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jesse/Downloads/ike


As you can see I have gotten closer. Any other ideas?

---

### Post by esvcv on 2013-02-03
That's perfect... you have successfully built / compiled the program, now you just need to install it :D

```
sudo make install
```

Once installed run the following to start the IKE daemon:

```
sudo iked start
```

And then start the front end application:

```
qikea
```

WINNER !

---

### Post by Aydos on 2013-02-03
> **esvcv said:**
> That's perfect... you have successfully built / compiled the program, now you just need to install it :D

```
sudo make install
```

Once installed run the following to start the IKE daemon:

```
sudo iked start
```

And then start the front end application:

```
qikea
```

WINNER !

We are a Go !!!

Thanks for helping with that. Was kind of fun.

However it does not show up as an installed program. Is there a way to make short cut for it in my apps or anything ?

---

### Post by Aydos on 2013-02-03
Ignore this post was a mistake on my part after loading it.

---

### Post by esvcv on 2013-02-03
Fantastic stuff, glad to have been of service !

You can create a Launcher from your Ubuntu desktop:

[LIST]
[*]Right-click on your desktop background and select *Create Launcher*
[*]Leave the **Type** as Application
[*]Give the **Name** whatever you want, eg. VPN, Shrew, Office, whatever you want
[*]Set the **Command **to: **qikea**
[*]Then if you're feeling saucy you can click on the little icon of the Rocket, and change it to the Shrew padlock (or whatever you want) - which is in that ike folder and then **/source/qikea/png/**
[*]Hit OK and you'll have a desktop icon to load qikea with !
[/LIST]
For Importing your .vpn file click on File > Import  :P

---

### Post by Aydos on 2013-02-03
> **esvcv said:**
> Fantastic stuff, glad to have been of service !

You can create a Launcher from your Ubuntu desktop:

[LIST]
[*]Right-click on your desktop background and select *Create Launcher*
[*]Leave the **Type** as Application
[*]Give the **Name** whatever you want, eg. VPN, Shrew, Office, whatever you want
[*]Set the **Command **to: **qikea**
[*]Then if you're feeling saucy you can click on the little icon of the Rocket, and change it to the Shrew padlock (or whatever you want) - which is in that ike folder and then **/source/qikea/png/**
[*]Hit OK and you'll have a desktop icon to load qikea with !
[/LIST]
For Importing your .vpn file click on File > Import  :P


You sir are amazing. Now I just got figure out why it says failed to attach key daemon when I try to long in.  Same file works on my wifes windows computer

---

### Post by esvcv on 2013-02-03
*Failed to attach to key daemon* usually means the IKE Daemon isn't running, did you run that command to start it before loading qikea...

```
sudo iked start
```

---

### Post by Aydos on 2013-02-03
> **esvcv said:**
> *Failed to attach to key daemon* usually means the IKE Daemon isn't running, did you run that command to start it before loading qikea...

```
sudo iked start
```

sudo iked start
!! : unable to open /etc/iked.conf


That is what I get. Also I installed gnome panel and made the launcher thanks for the tip

---

### Post by esvcv on 2013-02-03
That sounds like you might not have an iked.conf file..

Could you go into the /etc directory and check if iked.conf is there ?

```
cd /etc
ls ike*
```

If not there will hopefully be an *ike.conf.sample* instead, so just copy that and name it iked.conf

```
sudo cp iked.conf.sample iked.conf
```

And then try starting the daemon again:

```
sudo iked start
```

---

### Post by Aydos on 2013-02-03
Woot I am in a VPNed into my work network.

Thank you for all your help.

Hopefully anyone else trying to use Shrewsoft will come across the post were I think we have covered any issue you could potentially have lol.

One FINAL question lol.

Do I have to sudo start iked everytime? If so is there a way to add that to the launcher?

---

### Post by esvcv on 2013-02-03
Brilliant news - now you just need to do some work !!

The daemon appears to start automatically during boot up, at least for me.  So I don't need to run that command each time.

---

### Post by joske on 2013-02-05
My ppa contains the latest version for quantal.

Check jos-dehaes in launchpad.

---

### Post by baddison1 on 2013-03-01
> **Aydos said:**
> Ok I fixed the above problem with a 
sudo apt-get install flex

Then tried to install again and got a similar error about bison
sudo apt-get install bison

Then tried the install again and got

cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES
-- Using install prefix /usr ...
-- Using etc install path /etc ...
-- Using bin install path /usr/bin ...
-- Using sbin install path /usr/sbin ...
-- Using lib install path /usr/lib ...
-- Using man install path /usr/local/man ...
-- Using library -lpthread
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Performing Test NATT_FOUND
-- Performing Test NATT_FOUND - Success
-- Enabled NAT Traversal support ...
-- Looking for Q_WS_X11
-- Looking for Q_WS_X11 - found
-- Looking for Q_WS_WIN
-- Looking for Q_WS_WIN - not found.
-- Looking for Q_WS_QWS
-- Looking for Q_WS_QWS - not found.
-- Looking for Q_WS_MAC
-- Looking for Q_WS_MAC - not found.
-- Found Qt4: /usr/bin/qmake (found version "4.8.3") 
-- Enabled Client QT GUI support ...
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jesse/Downloads/ike


As you can see I have gotten closer. Any other ideas?

THis did not work for me.  I am getting many line errors when trying to run the install ? will be back with screen shot....

---

### Post by baddison1 on 2013-03-01
bernadette@E4300HJZH1L1:~/Downloads/ike$ cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES-- The CXX compiler identification is unknown
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.
-- Using install prefix /usr ...
-- Using etc install path /etc ...
-- Using bin install path /usr/bin ...
-- Using sbin install path /usr/sbin ...
-- Using lib install path /usr/lib ...
-- Using man install path /usr/local/man ...
-- Using library -lpthread
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Enabled NAT Traversal support ...
-- Enabled Client QT GUI support ...
-- Configuring incomplete, errors occurred!
bernadette@E4300HJZH1L1:~/Downloads/ike$ 

Not sure why the "CMAKE_CXX_COMPILER..." is not found???

---

### Post by baddison1 on 2013-03-01
NEVERMIND!!!  I ran

$ sudo apt-get install build-essential -y

then I re-ran the cmake command...and EVERYTHING works!!!  Thanks for the great information on this forum!!!

---

### Post by Heinzelmannchen on 2013-05-12
When running  ```
cmake -DCMAKE_INSTALL_PREFIX=/usr -DQTGUI=YES -DETCDIR=/etc -DNATT=YES 
```

I get
```
-- Using install prefix /usr ...
-- Using etc path /etc ...
-- Using lib path /usr/lib ...
-- Using man path /usr/local/man ...
-- Using binary /usr/bin/flex ...
-- Using binary /usr/bin/bison ...
-- Enabled NAT Traversal support ...
-- Could NOT find Qt3 (missing:  QT_QT_LIBRARY QT_INCLUDE_DIR) 
CMake Error at CMakeLists.txt:423 (message):
  Unable to locate required package : QT

```

Anyone know what to do?

---

