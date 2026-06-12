---
title: "Configure apt-get with proxy"
date: 2005-09-21
forum: General Help
---

### Post by gizmoz on 2005-09-21
Hello,
Does anyone know:
- How do I configure apt-get to work with a proxy?
- How do I configure kynaptic (not synaptic) to work with a proxy?
Thank you

---

### Post by mlomker on 2005-09-21
Put the following into your /etc/bash.bashrc file (after putting in the proper servername/IP and port number).  Just include the server/port if you have no authentication on your proxy server.

```

export http_proxy=http://user:password@my.proxy.server:port/
export ftp_proxy=http://user:password@my.proxy.server:port/

```

Add these lines, open a new root terminal, and then run your apt-get from the command line.

---

### Post by gizmoz on 2005-09-21
[QUOTE=mlomker]Put the following into your /home/username/.bashrc file (after putting in the proper servername/IP and port number).

```

export http_proxy=http://my.proxy.server:port/
export ftp_proxy=http://my.proxy.server:port/

```

I know that'll work if you add the lines, open a new Konsole prompt, and then launch Kynaptic from there.  Perhaps you'll have to put it into /etc/init.d/bootmisc.sh instead before it'll affect the whole system?  I haven't tested that.[/QUOTE]

Thanks mlomker for your reply. I tested both but it didn't work. Kubuntu has IP:192.168.0.130 and proxy (on win xp) has 192.168.0.60 port 808 so I entered at the end of  .bashrc:
export http_proxy=http://192.168.0.60:808/
export ftp_proxy=http://192.168.0.60:808/
Then I did the same in bootmisc.sh just before : exit 0 
And tried all combinations (only to .bashrc, only to bootmisc.sh, both) with no luck  :-|

---

### Post by mlomker on 2005-09-21
> And tried all combinations (only to .bashrc, only to bootmisc.sh, both) with no luck  :-|

I know that will work for apt-get from the command line because I [helped a guy](http://www.ubuntuforums.org/showthread.php?t=63223)  get it working using that method.  Perhaps you'll have to keep looking for a solution with Kynaptic.

I assume you rebooted after making these changes?

---

### Post by gizmoz on 2005-09-22
[QUOTE=mlomker]I know that will work for apt-get from the command line because I [helped a guy](http://www.ubuntuforums.org/showthread.php?t=63223)  get it working using that method.  Perhaps you'll have to keep looking for a solution with Kynaptic.

I assume you rebooted after making these changes?[/QUOTE]

You are absolutely right! 

At first I changed the files you mentioned and I was loged in as root (I have root login enabled) and it wasn't working (After I modified root/.bashrc too).

But I tried again now logged in as user (console -> sudo kynaptic) and worked fine (and sudo apd-get update worked too)!

Thank you very much!

---

### Post by vitek on 2006-02-17
A better solution is at [http://tim.suttonfamily.co.uk/timwiki/Ubuntu_basic_configuration_step_by_step](http://tim.suttonfamily.co.uk/timwiki/Ubuntu_basic_configuration_step_by_step)

<cite>
Set your apt configuration to use your proxy if needed
If you can only access the net via a proxy you will need to edit this file first and to do that you will need to open a terminal: 
Applications -> system Tools -> terminal  
sudo su -
cd /etc/apt
vim apt.conf.d/70debconf

that will edit the main debian apt configuration file, to which you should make the following addition: 
 

Acquire {
        http {
                Proxy "http://foouser:barpassword@wwwcache.rdg.ac.uk:8080/";
                // puoi anche giocare coi parametri della cache
                No-Cache "false";
                Max-Age "86400";
                No-Store "false";
        };
};

/!\ Note: Replace your username and password!
</cite>

---

### Post by lifeperfecti0n on 2006-02-17
Hi,
It seems that I have a similar problem..
[http://ubuntuforums.org/showthread.php?t=126871](http://ubuntuforums.org/showthread.php?t=126871)
i includred http_proxy in /etc/bash.bashrc and tried using cvs but it gives unknown host. Any ideas?:-k 
If there is a cvs conf file I would have to edit, where is it?
Actually I want to compile Cedega from source to prove linux is better than windows in gaming!:)

---

### Post by EvilSoccerFiend on 2007-08-22
When you set proxy variable (or any variable for that matter) in ~/.bashrc you do not need to reboot.  Simply type:
source ~/.bashrc

Also, remember that each user has their own .bashrc, so if this variable is not set system wide, you will need to add it to that users .bashrc (eg. /root/.bashrc).

---

