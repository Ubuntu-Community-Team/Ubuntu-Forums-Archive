---
title: "Help with Proftpd"
date: 2017-09-29
forum: General Help
---

### Post by jrpayne30040 on 2017-09-29
[COLOR=#333333]Hi Everyone,[/COLOR]

[COLOR=#333333]I am a very inexperienced Linux/Ubuntu guy and need some help. I have created a server that I am going to use for both an FTP server as well as a syslog server. I started with FTP and have installed Proftpd and Gadmin. Yes I have GUI loaded mainly because it cuts down the time on the learning curve for some things. Anyway, I have installed both of these and created a user and pointed that user to a directory that is not the program default. I did this with GAdmin and not in the conf file. When I try to test with this user, I get an error that states "Unable to set anonymous privileges". I didn't intend to have anonymous connection at all anyway. So ultimately what I want to do is have a user log in and use the directory that I point them to in Gadmin. I can do it with the conf file if need be but I am putting the ftp directories on a different drive than where the OS is installed. A drive with more space because of the contents of the ftp and syslogs. I hope that makes sense and someone knows where I am headed with this.[/COLOR]

---

### Post by TheFu on 2017-09-30
Welcome to the forums.

a) Don't use plain FTP.  This is a terrible protocol and should have died in 1995 with telnet.  
b) If you do use it as a plain FTP server, definitely DO NOT push syslog files onto it from other systems.  Plain FTP is just to non-secure to hold sensitive data, like syslogs.
c) The GUI doesn't cut down learning time. It teaches 10% of the stuff you need to know as an Admin.  You are missing all the power.  I know it is overwhelming - we've all been there. The best GUI tools only provide 20% of the capability of the CLI programs, but usually less.
d) GUIs change every few years, while the CLI versions seldom change.  I use the same methods today as I did 20 yrs ago.
e) GUIs open up security issues that wouldn't happen otherwise. That is the nature of X/Windows and webapps.

Learn the CLI and shell. Please.  These work over ssh on a modem from halfway around the world.  GUIs do not.

Might I suggest purging all FTP servers, install **openssh-server**, and use sftp.  There are great sftp clients for every networked platform. These are considered "secure" from anywhere in the world if keys are used, never passwords. With ssh (which is a way of life on Unix systems), you get scp, sftp for free.  Once the ssh-keys are setup, all of these (and rsync, rdiff-backup, and any other tool that uses libssh) will honor the keys.  You are both more convenient AND more secure.  When was the last time that happened? Hint - never.

If you are trying to setup sftp for hundreds of users and don't want to allow them ssh access too, there are techniques.  ssh can authenticate using LDAP for 50K users.

I know this isn't the answer you expected, but please learn from it.  
* [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

If you still want plain FTP server help, just tell me to go away. Hopefully someone else come along to help.

---

### Post by JKyleOKC on 2017-09-30
I respect both the knowledge in, and the intent of, the previous post, but there are actually some very good arguments in favor of using FTP -- the strongest of which (in my opinion) is its age. It's been around long enough for many of its vulnerabilities to have been identified long ago, and defenses for them to be developed and well-tested. Most of the weaknesses and insecurity, these days, results not from FTP as such, but from improper configuration of it.

And one of the reasons for improper configuration is the use of GUI tools to administer it. In that, I agree fully with TheFu!

Few, if any, of the GUI tools for FTP that I've seen even hint at the degree of control you can achieve with Proftpd. You can, for instance, set up individual hidden subdirectories for incoming data, outgoing data, and public access -- without hinting at all to the outside world that they exist. You can limit the command vocabulary that the server recognizes, and take away all ability to break out of the sandbox that you can create to eliminate almost all of the vulnerabilities (by restricting their effects to a tightly controlled subset of your server's resources.

While the on-line documentation you find at the Proftpd web site is fairly difficult to wade through, initially, it DOES tell you how to do all these things. A familiarity with the configuration process of the Apache web server will help greatly; I didn't fully grok the FTP material until being forced by other events to study Apache; then things became much less muddy.

And one very good reason for continuing to use FTP rather than SFTP is that almost all operating systems either include a client for it by default, or make available a simple client as a free download. Modern browsers seem to have such a client built in, for downloads. Like ASCII text files, it provides a common denominator for file transfer -- and not everyone has an SFTP client available.

As for a syslog server, I agree with TheFu. That data is just about the most sensitive on your system, so needs total protection. Putting the data, though not necessarily the server itself, on a large-capacity external drive that can be swapped out regularly will keep it much safer than it will be on any system that's always on the net!

---

### Post by HermanAB on 2017-10-01
Ayup, the advantage of plain old FTP is that it is simple.  It is not secure.  It doesn't even pretend to be secure.  However, if it is on a LAN, then there are various ways by which you can protect it a bit.  The simplest method is to separate the upload and download directories.

---

### Post by JKyleOKC on 2017-10-01
> **HermanAB said:**
> Ayup, the advantage of plain old FTP is that it is simple.  It is not secure.  It doesn't even pretend to be secure.  However, if it is on a LAN, then there are various ways by which you can protect it a bit.  The simplest method is to separate the upload and download directories.Yep, that's the first step: create separate directories and limit the commands available in each to the absolute minimum necessary for functionality. For my database recovery business, which often involves transfers in the gigabyte size range, I have to have a private server available to selected customers on demand. It has a write-only directory for all incoming traffic, to which only I have read permission (and that's NOT via the server), and for which the server cannot display any directory information, not even the directory's existence. There's a similar outgoing directory, where the server cannot write and again no directory data is available to the outside world. Finally, there's a public directory, and the server is configured to present ONLY this one (which has no write capability) to the world at large.

My firewalls indicate an average of slightly more than 1,000 invasion attempts daily. There's no evidence of any being successful, though I'm sure that anyone with enough determination could find a way through. I did get invaded once, more than 10 years ago, because I had left myself a backdoor so that I could do remote maintenance if need be -- and a bad guy found it. Removing that backdoor and permanently disabling most of the navigation commands in the server seems to have solved the problem, and having to reformat all my systems and restore from backups taught me to be more careful.

On the other hand, when I installed an automatic backup system controlled via SSH, it took less than a month for it to become compromised. Fortunately by that time I was sufficiently paranoid to have limited the damage to only one system rather than my entire little LAN.

Bottom line: if you maintain ANY sort of web presence that requires an open server, too much paranoia is not nearly enough!

---

### Post by TheFu on 2017-10-01
Nothing teaches security like being hacked.  

I've been hacked 3 times.  Only once on a network that I controlled and that was 15+ yrs ago.  There are certain services I will not allow on my networks - plain FTP is 2nd on the list.

Once was on a govt network in a lab environment.  This was long before NAT existed.

Last time was about 3 yrs ago, at a security conference where I was helping to run a NetKoTH contest.  My laptop was not a target, but just being on that LAN was enough.  It was a 100% patched, newly installed 2 days earlier, Ubuntu Server with openbox as the GUI. No DEs. Only network service up was ssh, with key-only remote logins and fail2ban enabled.  They didn't come in that way.  

The #1 security practice I know is to have 60+ days of versioned backups. For high-risk systems, 120 days or more.  Any plain FTP server is high risk in my book.

---

### Post by jrpayne30040 on 2017-10-02
Thankl you all for your advice and wisdom on the matter. I don't have a problem using sftp. Like i said in my post, I am a Linux newbie/very inexperienced. The GUI I installed because I wanted to be able to direct my uploads to a folder on a different drive that the one that the ubuntu install lives on. It was very easy to point to that folder using gadmin. However due to some of the things I have read here, I just wiped the server and am about to start from scratch and use sftp and just figure out how to point the users directories to the other drive via the cli. It is just something I am not familiar with yet and I was trying to get this thing up and going.

---

### Post by TheFu on 2017-10-02
So .... 

a) SOLVED?  If so, please mark the THREAD that way to help others.

b) Almost every Linux file manager supports sftp:// URLs, natively.  Basically, you can have access to your files from anywhere in the world because of this.  

c) For non-Unix users (there is only 1 major OS that falls into that group BTW), there is filezilla and WinSCP.  All Unix-like system have GUI or there is always scp, sftp, sshfs, or ssh directly.  These all use the same credentials, same ssh-keys, and same port.  It is extremely firewall friendly.  If you want to go crazy about security, forcing an elliptical encryption method for key exchange would be a step up, but realistically, the defaults with 4K keys are fine if you don't work for any secret govt agency doing stuff in a different country. ;)

d) For end users, you can setup **symbolic links** or force their HOME directory to be the location where they should drop files off or just after a connection, force their PWD to be changed to the directory they should be using.  Lots of options.  It is a best practice NOT to have the drop off and pick up in the same disk areas. There are lots of other security best practices for files being pulled if they contain images/media to prevent them from being used to attack other people.  BTW, sftp may not be the best solution for any specific problem. Just depends.

Being new to Unix-like systems is something everyone here has been through.  There is a very steep learning curve that lasts years.

---

