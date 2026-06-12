---
title: "xhost display"
date: 2017-06-16
forum: General Help
---

### Post by pkoukoulis-r on 2017-06-16
Hi

I am attempting to run xclock from the command line on Lubuntu:
My hosts file looks as follows:
[FONT=courier new]$ cat /etc/hosts[/FONT]
[FONT=courier new]127.0.0.1    localhost[/FONT]
[FONT=courier new]10.11.12.15     or[/FONT]

I've added the hostname, as well as the ip address to the xhost access list:
[FONT=courier new]$ xhost +10.11.12.15[/FONT]
[FONT=courier new]10.11.12.15 being added to access control list[/FONT]
[FONT=courier new]
[/FONT][FONT=courier new]$ xhost +or[/FONT]
[FONT=courier new]or being added to access control list[/FONT]



Display variable I've set as:
[FONT=courier new]$ DISPLAY=or:0.0; export DISPLAY[/FONT]

Hostname is:
[FONT=courier new]$ hostname
or
[/FONT]
when attempting to run xclock, I get the following error:
[FONT=courier new]$ xclock[/FONT]
[FONT=courier new]Error: Can't open display: or:0.0[/FONT]




Can anybody suggest how I can run xclock ?

Thanks

---

### Post by TheFu on 2017-06-16
```
export DISPLAY=:0
xclock &
```

Don't make it hard.  Of course, you must be running an X/Server. This will never work on a console.

I would stay away from using hostnames that match keywords for languages.
No need for xhost + anything if you are sitting on the same machine where the x-client and x-server are running. If that isn't the situation, best to use **ssh -X** from the X/Server machine to the X/client machine. That will automatically set the DISPLAY for you and tunnel it through ssh.  There is an X-Forwarding setting on the ssh-server that must be enabled. I think that is enabled by default.  It is in the /etc/ssh/sshd_config file.

Clear as mud?

---

### Post by pkoukoulis-r on 2017-06-17
thanks for the reply. "*clear as mud?*" somewhat!
I was merely attempting to follow [these]("https://community.oracle.com/thread/2358808") instructions 

I am running a bash shell on the same machine. I am not using ssh from a remote client.

[FONT=courier new]oracle@or:/tmp/database$ export DISPLAY=:0[/FONT]
[FONT=courier new]oracle@or:/tmp/database$ xclock &[/FONT]
[FONT=courier new][1] 2963[/FONT]
[FONT=courier new]oracle@or:/tmp/database$ No protocol specified[/FONT]
[FONT=courier new]Error: Can't open display: :0[/FONT]

Still the same error message based on your idea.

---

### Post by TheFu on 2017-06-17
If you aren't running an X/Server, then nothing you do will make any difference.
So, a few things.

You are running a supported Lubuntu release? 

You are booted into a graphical environment, running a window manager?

You opened a terminal - like an xterm?  What is it?

At the terminal, the DISPLAY should already be set correctly - what does env $DISPLAY show?

It works on all my systems (btw, I was an X/Windows programmer 25+ yrs ago).
It should work on any system running X/Windows with the xclock example application.  If you can run **xterm -sb** from a terminal and get another, then there is no reason xclock shouldn't work.

---

### Post by pkoukoulis-r on 2017-06-17
xclock works when I run it in user account that I installed Lubuntu with (albeit with a warning message), but the issue is when I su to another user:

$ xclock
Warning: Missing charsets in String to FontSet conversion
$ su oracle
Password: 
$ echo $DISPLAY
:0.0
$ xclock
No protocol specified
Error: Can't open display: :0.0

---

### Post by TheFu on 2017-06-17
You can't do that.

---

### Post by pkoukoulis-r on 2017-06-17
ok, thanks. I'll switch back to the original unix account.

---

### Post by TheFu on 2017-06-17
> **pkoukoulis-r said:**
> ok, thanks. I'll switch back to the original unix account.

Xauth is a really weenie security model, but there are ways around it if you really need to.  

root running X/Windows of any sort is a bad idea from a security standpoint.  You should be able to use the GUI-version of sudo.  99.9999% of the time, this is a terrible idea and will cause unintended issues that someone new-to-Unix isn't prepared to fix. All of these things come from the "if you have to ask, then you shouldn't do it" pile-of-questions.

---

### Post by steeldriver on 2017-06-17
xhost works, for me:

```

steeldriver@xenial-vm:~$ su - testuser
Password:
testuser@xenial-vm:~$ xclock
No protocol specified
Error: Can't open display: :0.0
testuser@xenial-vm:~$ exit
logout

```

but 

```

steeldriver@xenial-vm:~$ xhost +si:localuser:testuser
localuser:testuser being added to access control list
steeldriver@xenial-vm:~$
steeldriver@xenial-vm:~$ su - testuser
Password:
testuser@xenial-vm:~$ xclock

```
(works)

In general, the syntax is family:name, so if you want to allow acces to all users on the localhost, the syntax is:
```

steeldriver@xenial-vm:~$ xhost +local:
non-network local connections being added to access control list

```

or from a specific host by IPv4:

```

steeldriver@xenial-vm:~$ xhost +inet:192.168.1.11
192.168.1.11 being added to access control list

```

You can allow wide open access with plain `xhost +` but I don't recommend it for obvious security reasons

---

### Post by TheFu on 2017-06-17
Very cool steeldriver!

From the xhost manpage:
```
NAMES
       A complete name has the syntax ``family:name'' where the  families  are
       as follows:

       inet      Internet host (IPv4)
       inet6     Internet host (IPv6)
       dnet      DECnet host
       nis       Secure RPC network name
       krb       Kerberos V5 principal
       local     contains only one name, the empty string
       si        Server Interpreted

       The family is case insensitive.  The format of the name varies with the
       family.
...
       The  local family specifies all the local connections at once. However,
       the server interpreted address "si:localuser:username" can be  used  to
       specify a single local user. (See the Xsecurity(7) manual page for more
       details.)
```

The 'si' meaning is a little fuzzy to me.  My 14.04 install doesn't have section 7's Xsecurity manpage. Guess using an online source is needed.  Is this something new?

---

### Post by pkoukoulis-r on 2017-06-17
great, many thanks, 

so the above suggestion by steeldriver did the trick:

$ xhost +local:
$ su oracle
$ xclock

---

### Post by steeldriver on 2017-06-17
man 7 Xsecurity doesn't really say a whole lot more, just:

```

       Server Interpreted
              The  Server  Interpreted  method  provides  two strings to the X
              server for entry in the access control list.  The  first  string
              represents the type of entry, and the second string contains the
              value of the entry.  These strings are interpreted by the server
              and  different  implementations and builds may support different
              types of entries.  The types supported in the sample implementa&#8208;
              tion  are defined in the SERVER INTERPRETED ACCESS TYPES section
              below.   Entries of this type can be manipulated via xhost.  For
              example to add a Server Interpreted entry of type localuser with
              a value of root, the command is xhost +si:localuser:root.

```

Not sure why it's on my 14.04 system not yours - the manpage is provided by package `xorg-docs-core` - perhaps that got pulled in because I have some X11 dev packages installed

---

### Post by TheFu on 2017-06-17
Checked a few other systems here ... none of the 14.04 systems have it, but my only 16.04 desktop does.  Interesting.  I install "server" and add the X stuff I want, to it isn't pulled in by the minimal X dependencies, I suppose.

Never noticed anything unexpected missing before.  Should probably update my ansible desktop-built playbook for this, just in time for X11 to be replaced. ;)

It has been a few years since I did any X programming, even manually building something with X dependencies.

Main thing is that the OP got a working solution AND I learned a little more.

---

