---
title: "Newbie Help - Installing Tomcat"
date: 2007-10-30
forum: General Help
---

### Post by tberman333 on 2007-10-30
Hello there.  I am very new to Ubuntu (and Linux).  I installed it for the first time yesterday.  One of the main things I am going to use it for is running a music server via Tomcat.  I have run this successfully in Windows, but now I am having a hard time getting Tomcat working with Ubuntu.

First I tried to just install Tomcat 5.5 from Synaptic (unfortunately all that was available there was 5.5 even though the most recent version of Tomcat is v6.0).  Anyway, that install did not work at all (I could not figure out where to find Tomcat or how to start it).

My next step was to look in these forums and do a Google search.  I found many different sites telling me how to install Tomcat 5.5 and 6.  Some sites where Ubuntu specific and some were just how to install in Linux.

Like I said, I am very new and although I can follow directions well (and have read a little documentation on how Ubuntu/Linux works), all of these help sites just confused me.  I actually tried to follow the instructions on one of them, but it made my system crash (to the point where I had to reinstall Ubuntu).

I was hoping that someone could just point me in the direction of a site that explains (step-by-step) how to get Tomcat working.  Any help is really appreciated!

Thanks!

---

### Post by kah00na on 2007-10-31
If you are running 7.10 Gutsy Gibon, you could use the search tool to try and find the executable or you can open a terminal and type:

```
find / -name ______   
```

( replace "_" with the executable you are looking for)

---

### Post by tberman333 on 2007-10-31
> **kah00na said:**
> If you are running 7.10 Gutsy Gibon, you could use the search tool to try and find the executable or you can open a terminal and type:

```
find / -name ______   
```

( replace "_" with the executable you are looking for)

I am using 7.10 Gusty Gibson.  And I think I was confusing in my question.  I was able to find Tomcat in Synaptic, but there was only Tomcat 5.5 (not Tomcat 6) and after I ran the install from there I could not find Tomcat on my system to start it.

Based on what I have read (through my web searches), Tomcat does not install correctly when run from Synaptic.  Can anyone point me in the right direction for installing this via terminal (or directly from the binary download on their website)?  And then how to run Tomcat as a service that will start when I start Ubuntu?

Thanks!

---

### Post by Maestro23 on 2007-10-31
> **tberman333 said:**
> I am using 7.10 Gusty Gibson.  And I think I was confusing in my question.  I was able to find Tomcat in Synaptic, but there was only Tomcat 5.5 (not Tomcat 6) and after I ran the install from there I could not find Tomcat on my system to start it.

Based on what I have read (through my web searches), Tomcat does not install correctly when run from Synaptic.  Can anyone point me in the right direction for installing this via terminal (or directly from the binary download on their website)?  And then how to run Tomcat as a service that will start when I start Ubuntu?

Thanks!

Please provide the link to the website.

---

### Post by tberman333 on 2007-10-31
> **Maestro23 said:**
> Please provide the link to the website.

This is the site to download the version I am trying to install.

[http://tomcat.apache.org/download-60.cgi](http://tomcat.apache.org/download-60.cgi)

---

### Post by Maestro23 on 2007-10-31
> **tberman333 said:**
> This is the site to download the version I am trying to install.

[http://tomcat.apache.org/download-60.cgi](http://tomcat.apache.org/download-60.cgi)

Never used the program myself.  I downloaded the .tar.gz file.  There is a text document called "Running" in the extract folder.  Contains program requirements, Installation instructions, etc...

Once you download the .tar.gz, you can right click on it and extract.  You will find the document I'm referring to.  Going to take some reading/digesting the info on your part though.

6.0 Documentation link: [http://tomcat.apache.org/tomcat-6.0-doc/index.html](http://tomcat.apache.org/tomcat-6.0-doc/index.html)

*Maybe someone who has used Tomcat before, will see your thread. Give it some time though.

Good luck man.:guitar:

---

### Post by meindian523 on 2007-10-31
If Tomcat is a music server,and if it has a GUI,most probably it would be found in Applications>>Sound and Video.Kinda logical,ain't it?:)

---

### Post by tberman333 on 2007-10-31
> **Maestro23 said:**
> Never used the program myself.  I downloaded the .tar.gz file.  There is a text document called "Running" in the extract folder.  Contains program requirements, Installation instructions, etc...

Once you download the .tar.gz, you can right click on it and extract.  You will find the document I'm referring to.  Going to take some reading/digesting the info on your part though.

6.0 Documentation link: [http://tomcat.apache.org/tomcat-6.0-doc/index.html](http://tomcat.apache.org/tomcat-6.0-doc/index.html)

*Maybe someone who has used Tomcat before, will see your thread. Give it some time though.

Good luck man.:guitar:

Thanks!  I will work on it a little more... maybe post here if I have more questions!

---

### Post by tberman333 on 2007-10-31
> **meindian523 said:**
> If Tomcat is a music server,and if it has a GUI,most probably it would be found in Applications>>Sound and Video.Kinda logical,ain't it?:)

Tomcat is not a music server, it is a web application server (I use a web application called subsonic as the music server.

Thanks though!

---

### Post by Prospero2006 on 2007-10-31
I run tomcat on several machines, and I can vouch for the fact it isn't easy to set up.
However, once you get it set up, it's very nice to have around. I love programming in java.

Anyway, you download the Tomcat server and unzip it. 
For me I have this script set up to run the thing:

```

#!/bin/sh
#
# Startup script for Tomcat
#

case "$1" in
 start)
    echo -n "Starting Tomcat"
    JAVA_HOME="/downloads/jdk1.5.0_10" ; export JAVA_HOME &&
/downloads/apache-tomcat-5.5.17/bin/startup.sh
    ;;
 stop)
    echo -n "Stopping Tomcat"
    JAVA_HOME="/downloads/jdk1.5.0_10" ; export JAVA_HOME &&
/downloads/apache-tomcat-5.5.17/bin/shutdown.sh
    ;;
 restart)
    $0 stop
    $0 start
    ;;
 *)
    echo "Usage: $0 {start|stop|restart}"
    exit 1
esac
 
```

Java home points to jdk1.5.0_10 in my case. That one seems to work where others failed with my installation. 
The apache-tomcat-5.5.17 directory was unzipped in the 'downloads' directory.

So, you'll have to edit that script up to get it running, but that should be a step in the right direction.

Pros

---

### Post by tberman333 on 2007-10-31
Well, after more research, I found two sets of instructions that I was able to combine to get this installed (and working correctly).  These instructions are taken from these two places:

[http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat+install]("http://ubuntuforums.org/showthread.php?t=420034&highlight=tomcat+install")
[http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/]("http://www.howtogeek.com/howto/linux/installing-tomcat-6-on-ubuntu/")

[SIZE="5"]***_Thank you to the authors of both of those instruction for all of the information._***[/SIZE]

Anyway, here is how I did it:

1.  Installed Java from Synaptic.  I chose these three applications (after doing a search for Java):
```
sun-java6-jdk
sun-java6-jre
sun-java6-plugin
```
I am not sure if the plugin was needed, but I installed it anyway.

2. in Terminal downloaded the binary file with:
```
wget http://apache.hoxt.com/tomcat/tomcat-6/v6.0.14/bin/apache-tomcat-6.0.14.tar.gz
```

3.Then in Terminal extracted the tar with:
```
tar xvzf apache-tomcat-6.0.14.tar.gz
```

4.Next I moved Tomcat to a folder in usr/local with:
```
sudo mv apache-tomcat-6.0.14 /usr/local/tomcat
```

5.Then I used gedit to add JAVA_HOME to the .bashrc file
```
sudo gedit ~/.bashrc
```
Add this code to the file:
```
#set JAVA_HOME
export JAVA_HOME=/usr/lib/jvm/java-6-sun
```
save and exit

6.Log out of Ubuntu and log back on.

7.Start Tomcat
```
sudo /usr/local/tomcat/bin/startup.sh 
```

8.Check that install worked by going here in web browser:
[http://localhost:8080/]("http://localhost:8080/")

9.Stop Tomcat
```
sudo /usr/local/tomcat/bin/shutdown.sh
```

10.Change Tomcat admin user/password (this allows you to manage Tomcat) :
```
sudo gedit /usr/local/tomcat/conf/tomcat-users.xml
```
Between <tomcat-users> and </tomcat-users> enter this line:
```
<user username="your username" password="your password" roles="admin,manager"/
```>

[SIZE="4"]**Make Tomcat run as a service that starts when Ubuntu is started:**[/SIZE]

1.Crate a file called tomcat in init.d with the startup/shutdown script:
```
sudo gedit /etc/init.d/tomcat
```

Paste this script:
```
# Tomcat auto-start
#
# description: Auto-starts tomcat
# processname: tomcat
# pidfile: /var/run/tomcat.pid 
export JAVA_HOME=/usr/lib/jvm/java-6-sun 
case $1 in
start)
	sh /usr/local/tomcat/bin/startup.sh
	;; 
stop) 
	sh /usr/local/tomcat/bin/shutdown.sh
	;; 
restart)
	sh /usr/local/tomcat/bin/shutdown.sh
	sh /usr/local/tomcat/bin/startup.sh
	;; 
esac 
exit 0
```

2.Make the script executable
```
sudo chmod 755 /etc/init.d/tomcat
```

3.Link the script to the startup folders with a symbolic link. Execute these two commands:
```
sudo ln -s /etc/init.d/tomcat /etc/rc1.d/K99tomcat
```
```
sudo ln -s /etc/init.d/tomcat /etc/rc2.d/S99tomcat
```

After that Tomcat was working for me and it started when Ubuntu started!

:guitar:

---

