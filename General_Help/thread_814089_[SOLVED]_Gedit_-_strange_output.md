---
title: "[SOLVED] Gedit - strange output"
date: 2008-05-31
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-05-31
What's wrong with Gedit ?
```
$ gedit
Usage:program_name [address][:port]Usage:program_name [address][:port]$
```

---

### Post by pointone on 2008-05-31
What happens if you run:

```
command gedit
```

---

### Post by LinuX-M@n1@k on 2008-05-31
Same thing

---

### Post by LinuX-M@n1@k on 2008-06-01
Anyone else have this bug ?

---

### Post by pbpersson on 2008-06-01
I don't have my Hardy Heron machine running right now and I should really get to bed - I am typing on Gutsy Gibbon

However, if you look in the /usr/bin directory, there are a bunch of files.  These are usually symbolic links or shell scripts that allow your machine to run the associated program.

If you recognize some of them as applications you use, try typing their names at the command prompt as well and see if they function.

I'm wondering if the /usr/bin directory is no longer in your path....or if the symlink for gedit is missing or damaged.

However, that is a very strange error message you are seeing.  :confused:

---

### Post by LinuX-M@n1@k on 2008-06-01
```
$ cd /usr/bin
$ ll gedit pidgin
-rwxr-xr-x 1 root root 600832 2008-04-08 18:00 gedit
-rwxr-xr-x 1 root root 846872 2008-04-09 23:48 pidgin
$ ./pidgin
$ ./gedit
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]$
```
I get this message only when I close Gedit. As you can see, when I close Pidgin I don't get any messages.
And it's the same thing if I run it as root.
```
$ su
Password:
# pwd
/usr/bin
# ./pidgin
# ./gedit
Usage:program_name [address][:port]Usage:program_name [address][:port]# 
```
Edit: This is new:
```
$ firefox
Usage:program_name [address][:port]Usage:program_name [address][:port]Usage:program_name [address][:port]$
```

---

### Post by CameO73 on 2008-06-01
I have no idea what's causing this. But you're not alone (and it's probably not limited to gedit) ... just take a look at these Google results:
```
http://www.google.com/search?hl=en&pwst=1&q=Usage:program_name+[address][:port]&start=0&sa=N
```
[]("http://www.google.com/search?hl=en&pwst=1&q=Usage:program_name+") 
So, is this a bug or a Linux virus? :-k

---

### Post by geirha on 2008-06-01
> **CameO73 said:**
> I have no idea what's causing this. But you're not alone (and it's probably not limited to gedit) ... just take a look at these Google results:
```
http://www.google.com/search?hl=en&pwst=1&q=Usage:program_name+[address][:port]&start=0&sa=N
```
[]("http://www.google.com/search?hl=en&pwst=1&q=Usage:program_name+") 
So, is this a bug or a Linux virus? :-k

That google-search showed alot of cases related to sound, esd was mentioned several times, so I looked at the source of esound, and lo and behold
```

$ apt-get source esound
[...cut...]
dpkg-source: extracting esound in esound-0.2.38
[...cut...]
$ grep -R 'Usage:program_name' esound-0.2.38/
esound-0.2.38/esdlib.c:         printf ("Usage:program_name [address][:port]");

```

Certainly an identical string at least.

---

### Post by CameO73 on 2008-06-01
Nice find! I did some more digging in the code and found that that message only appears if IPv6 is enabled, and the [getaddrinfo]("http://linux.about.com/library/cmd/blcmdl3_getaddrinfo.htm") call fails. I have no idea why that happens (you would have to know the exact failure code) ... but it's probably network related. 

So ... what's the output from this command:
```
ip a | grep inet6
```Have you made any changes to network related stuff (firewall, disabling protocols, ...)? Or perhaps some ESD configuration changes?

I'm really grasping at straws here, since I know next to nothing about ESD, but it's an interesting problem.

---

### Post by LinuX-M@n1@k on 2008-06-01
Fixed.
```
$ gedit
$ firefox
$
```
The problem seems to occurred yesterday while I was installing Quake4. I had to edit the /etc/hosts file in order to accept any CD-Key. I changed the line "127.0.0.1 localhost" to "127.0.0.1 q4master.idsoftware.com". Now I changed it back to localhost and I don't get this message anymore.

Marking as Solved!

PS:
@ geirha:
Thanks for the "grep -R" command =]. I was looking for something like this.

---

