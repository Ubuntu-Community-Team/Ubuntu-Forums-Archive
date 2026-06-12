---
title: "secure reverse vnc connection"
date: 2007-03-07
forum: General Help
---

### Post by bradleyd on 2007-03-07
Hello,
I have been trying to get this to work and have come up short. I basically am using reverse connection to remote assist linux desktops. I am using vncviewer -listen on heldesk server.
On the client side I am using a gui app that basically calls x11vnc -connect helpdesk.server.com.
all is well but no security. I have thought of using stunnel, but had other problems with that. than I thought to use ssh tunnel. I cant get ssh tunnel for reverse connection to work. any help would greatly be appreciated.
Thanks in advance.

---

### Post by krunge on 2007-03-07
You may find some useful helpdesk mode usage here: [http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick") i.e. for stunnel SSL connections.

You can skip the wget/curl stuff if you have the materials and script already downloaded or available via nfs.

For the reverse SSH connections it is described here: [http://www.karlrunge.com/x11vnc/#tunnelling]("http://www.karlrunge.com/x11vnc/#tunnelling") (example script #2).

Basically it is just this:
```
ssh -t -R 5500:localhost:5500 user@machine 'x11vnc -display :0 -localhost -connect_or_exit localhost'
```
run on machine "helpdesk.server.com" (where a vncviewer -listen is waiting).  Note the "-R" instead of the "-L" used in forward tunnelling.

Of course due to X auth permissions the x11vnc must be run as the user owning the desktop.  Maybe you do that separately, in which case the ssh doesn't need to start x11vnc (but the ssh will need to take place before x11vnc -connect is run otherwise the tunnel won't be up for the reverse connection yet).

---

### Post by bradleyd on 2007-03-07
tried that link for stunnel, but kept getting can't read /etc/stunnel/stunnel.pem. tried it for about a day. Will try other suggestion and post back. thanks.

---

### Post by bradleyd on 2007-03-07
ok on helpdesk server machine i have vncviewer --listen running. 
Then on the same machine I type ssh -t -R 5500:localhost:5500 [email]help@helpdesk.server.com[/email] 'x11vnc -display :0 -localhost -connect_or_exit localhost'

It then displays the helpdesk.server.com desktop and starts cascading the vnc window multiple times.

---

### Post by krunge on 2007-03-08
> ok on helpdesk server machine i have vncviewer --listen running.
Then on the same machine I type ssh -t -R 5500:localhost:5500 [email]help@helpdesk.server.com[/email] 'x11vnc -display :0 -localhost -connect_or_exit localhost'


Not "help@helpdesk.server.com", you don't want to run x11vnc there...  It needs to be
something like "joe@joes-workstation" (N.B. x11vnc must be run as user "joe" to view his desktop).

You mentioned that you can have the user click on a button to start x11vnc on his workstation.
In that case you would only need to do:

```
ssh -t -R 5500:localhost:5500 somebody@joes-workstation 
``` **BEFORE** the user clicks to start x11vnc.

Regarding the /etc/stunnel/stunnel.pem error, why don't you post the full command you ran and the full output from it?

---

### Post by bradleyd on 2007-03-08
ok that works. the only problem with that is the client(joe) would have to ssh server enabled on their end. Also I would need to have their password. Could I execute 
 ssh -L 5501:127.0.0.1:5500 [email]help@helpdesk.server.com[/email] on joe's machine then execute
x11vnc --connect localhost:5500 on joe's machine to connect in tunnel?
thanks again.

---

### Post by krunge on 2007-03-08
> Could I execute
ssh -L 5501:127.0.0.1:5500 [email]help@helpdesk.server.com[/email] on joe's machine then execute
x11vnc --connect localhost:5500 on joe's machine to connect in tunnel?

You mean joe clicks on a button and those two commands get run as him (in that order) on his workstation?  Yes that would work (assuming "vncviewer -listen" is already running on the help side).

But it wouldn't be "5501" it would be "5500" (that 5501 from the guide is related to the SSL stunnel mode, not the SSH you are using here).

You may want to put a "sleep" pause between the two commands to make sure the ssh tunnel is up before x11vnc starts.  A trick I use for doing this is:
```
ssh -f -t -L 5500:127.0.0.1:5500 help@helpdesk.server.com "sleep 15"
x11vnc -connect_or_exit localhost:5500
``` which (the -f) makes sure the ssh is up before x11vnc is run.

Also, this would require joe to be able to log into helpdesk.server.com as user "help".  Is that set up?  He would need the password for user "help", or have his key in help's ~/.ssh/authorized_keys, or "help" has no password...  This will also work if he logs in as "joe" on helpdesk.server.com which might be the simplest way to proceed if the user accounts are on that server.

Otherwise I suggest making a stripped down account on helpdesk.server.com that all user's ssh to.  Sometimes I give this stripped down user shell /bin/false and use the ssh -N option (i.e. it just does port redir, no commands. read the ssh(1) manpage for details).

---

### Post by bradleyd on 2007-03-08
that's what I thought. thanks for the sleep tip. I was trying to think of a way to bundle the pub key in heldesk's authorized_keys to joe's machine via the application. Basically have ssh use that pub key I provide in the application so joe does not need to enter password to connect. I am trying to make this so joe's mom can do this. I have attached a pic for the ui.

---

### Post by krunge on 2007-03-08
I believe the application would have to carry around the **private** key, not the **public** one, to be able to log into helpdesk.server.com for free.  The private key would also need to have no passphrase to survive the joe's-mom limit.

I guess that would be OK if you did this for a stripped down /bin/false account (e.g. [email]redir@helpdesk.server.com[/email] has shell /bin/false, or /bin/true for that matter)... but that is a little risky and you will need to think about it.

This is where the SSL stunnel I describe at [http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick")  comes in handy: no ssh unix accounts are involved.  Even still, there is some risk in that with man in the middle unless you carefully distribute certs...

---

### Post by bradleyd on 2007-03-08
for stunnel I just apt-getinstall stunnel4.
then I followed these directions here [http://www.karlrunge.com/x11vnc/#faq-singleclick](http://www.karlrunge.com/x11vnc/#faq-singleclick)
By default Ubuntu does not create stunnel.pem. Following these instructions on the helpdesk server i execute stunnel4 stunnel.cfg and I get /etc/stunnel/stunnel.pem: No such file or directory (2)
But on the joe's side I execute stunnel4 stunnel.conf and get:
 stunnel4 stunnel.conf <---this is the stunnel.conf from the website**********

2007.03.08 14:07:32 LOG6[2156:3083359920]: PRNG seeded successfully
2007.03.08 14:07:32 LOG5[2156:3083359920]: stunnel 4.15 on i486-pc-linux-gnu with OpenSSL 0.9.8b 04 May 2006
2007.03.08 14:07:32 LOG5[2156:3083359920]: Threading:PTHREAD SSL:ENGINE Sockets:POLL,IPv6 Auth:LIBWRAP
2007.03.08 14:07:32 LOG6[2156:3083359920]: file ulimit = 1024 (can be changed with 'ulimit -n')
2007.03.08 14:07:32 LOG6[2156:3083359920]: poll() used - no FD_SETSIZE limit for file descriptors
2007.03.08 14:07:32 LOG5[2156:3083359920]: 500 clients allowed

seems to run ok on joe's side.

---

### Post by krunge on 2007-03-08
> By default Ubuntu does not create stunnel.pem. Following these instructions on the helpdesk server i execute stunnel4 stunnel.cfg and I get /etc/stunnel/stunnel.pem: No such file or directory (2)

Ah, thanks for pointing this out.  I only tested running stunnel as root on a system that had  a /etc/stunnel/stunnel.pem.

I've modified the [http://www.karlrunge.com/x11vnc/#faq-singleclick]("http://www.karlrunge.com/x11vnc/#faq-singleclick") page to mention this, and also provides a workaround using x11vnc to generate the pem cert+key (openssl(1) command needs to be installed).

---

### Post by bradleyd on 2007-03-08
The update looks good. When I type   x11vnc -sslGenCert server self:mystunnel on Dapper, x11vnc starts and spits out it's usual output except I get this error:

5 *** unrecognized option(s) ***
08/03/2007 19:52:25     [1]  -sslGenCert
08/03/2007 19:52:25     [2]  server
08/03/2007 19:52:25     [3]  self:mystunnel
08/03/2007 19:52:25 For a list of options run: x11vnc -opts
08/03/2007 19:52:25 or for the full help: x11vnc -help
 It does not ask me the stunnel questions(state, city, etc..)
thanks again for your help.

---

### Post by krunge on 2007-03-08
Whoops, sorry x11vnc 0.8.3 or 0.8.4 is needed for this feature.

You can find some info on making them manually here: [http://www.stunnel.org/faq/certs.html]("http://www.stunnel.org/faq/certs.html") or using his CGI service: [http://www.stunnel.org/pem/]("http://www.stunnel.org/pem/").  Also my viewer frontend [ssvnc]("http://www.karlrunge.com/x11vnc/enhanced_tightvnc_viewer.html") can make self-signed certs too (Certs -> Create Certificate).

---

### Post by bradleyd on 2007-03-08
will try ssvnc, I tried the cgi script and it gives me an error.(can't think what it is right know)I wonder if it would be easier to build from source?The only thing I would have to repack it for each machine. Sometime's Joe uses Fedora or Suse or Slackware.etc..
Although after I get the stunnel.pem file, can i use x11vnc that comes stock in ubuntu or other distros?

---

### Post by bradleyd on 2007-03-09
I think I got it to work. what I did is on Joe's machine I did stunnel4 stunnel.conf &
then on helpdesk.server.com I downloaded your ssvnc. could not get gui to come up.(got unknown option"-state" while executing ssvnc.tcl error)so I copied the vnccert.pem file under bin/ to /etc/stunnel/stunnel.pem. Then I executed sudo stunnel4 stunnel.cfg & (just like your instructions [http://www.karlrunge.com/x11vnc/#faq-singleclick)Then](http://www.karlrunge.com/x11vnc/#faq-singleclick)Then) on helpdesk.server.com I issue vncviewer --listen. now back on Joe' machine I execute:
x11vnc -connect localhost:5500 -rfbport 0 -nopw and a reverse connection happens. My only question is how do i know it is using the stunnel? I know x11vnc -connect localhost:5500 -rfbport 0 -nopw says localhost so I am assuming it is using stunnel.
Thanks again.
Brad

---

### Post by krunge on 2007-03-09
> I wonder if it would be easier to build from source?

Yes, stunnel is an easy build.

> The only thing I would have to repack it for each machine. Sometime's Joe uses Fedora or Suse or Slackware.etc..

This is a problem I am facing with stunnel for a different deployment.  Linux compatibility is not so great...  There has been a recent change from libssl/libcrypto  0.9.7 -> 0.9.8.  Newer distros only include 0.9.8, so if you have apps built against 0.9.7 they break on the newer distros. You have to tell the user to install a 0.9.7 compatibility version (if their distro has it) or hack a library symlink.  This is a show-stopper for general deployment in my opinion.

So I've been playing with building a single stunnel binary for use on all Linuxes that statically links /usr/lib/libssl.a and /usr/lib/libcrypto.a so it can carry those libraries bolted on to it, rather than being suprised on some distros.  It seems to work fine.  I put the details here [http://www.karlrunge.com/x11vnc/#libssl-problems]("http://www.karlrunge.com/x11vnc/#libssl-problems")

> can i use x11vnc that comes stock in ubuntu or other distros?

I'm not sure what you mean... do you mean your app assumes /usr/bin/x11vnc is installed? Or  do you pre-install it on all of the machines?  Safest would be to bundle x11vnc with your quick connect app (as with the stunnel), but then you face the same problem with libssl, etc above. The Ubuntu x11vnc binary currently doesn't use libssl, so maybe it is less of a problem...

> My only question is how do i know it is using the stunnel? I know x11vnc -connect localhost:5500 -rfbport 0 -nopw says localhost so I am assuming it is using stunnel.

On both sides you can use netstat(1) and lsof(1) to make sure the connections are going thru the two stunnels.  I suggest "netstat -ante" and "lsof -c x11vnc", "lsof -c stunnel", etc.  Also check the stunnel log output (both sides).  If that is not enough you can sniff the wire with tcpdump or ethereal.

---

### Post by bradleyd on 2007-03-09
I guess I will bundle stunnel4 with the application. I am using                                   x11vnc 0.8.2-1 joe's end and  x11vnc  0.7.1-5 on helpdesk.server.com end. This is the netstat output I have pertaining to the test ip's:
tcp        0      0 192.168.19.57:45638     192.168.19.44:5501      ESTABLISHED1000 

my stunnel.cfg file on help server i added:
cert = /home/myusername/ssvnc/bin/vnccert.pem
then ran stunnel4 stunnel.cfg &
on joe's side added:
 CAfile = /home/myusername/Desktop/ssvnc/bin/vnccert.pem
 verify = 2
to stunnel.conf. ran stunnel4 stunnel.conf  and it still connected?
there is no stunnel.pem on both machines(there is but renamed them)
Does this all sound right?

---

### Post by bradleyd on 2007-03-09
used same configuration as last post but this time i used the stunnel bundled in your ssvnc folder(Linux.i686.newer)./stunnel /home/myusername/stunnel.conf
I used the gui to create the vnccert.pem file. The created one is on Joe's side. Do I have to copy the same vnccert.pem file to helpdesk side?
I could just bundle your ssvnc folder with application and use that stunnel.
sorry for all the questions, thanks for all your help.

---

### Post by krunge on 2007-03-09
> I am using x11vnc 0.8.2-1 joe's end and x11vnc 0.7.1-5 on helpdesk.server.com end.

You never run x11vnc on helpdesk.server.com, right?  Only on the users' desktops (joe, etc.)

> my stunnel.cfg file on help server i added:
cert = /home/myusername/ssvnc/bin/vnccert.pem
then ran stunnel4 stunnel.cfg &
on joe's side added:
CAfile = /home/myusername/Desktop/ssvnc/bin/vnccert.pem
verify = 2
to stunnel.conf. ran stunnel4 stunnel.conf and it still connected?
there is no stunnel.pem on both machines(there is but renamed them)
Does this all sound right?

We need to describe more carefully what you want to do SSL authentication-wise.

The minimal stunnel setup has only an stunnel.pem on the helpdesk.server.com side and no pem on joe's side (and hence no CAfile = or verify = on joe's side).

This protects against passive sniffing attacks, but does not protect against man-in-the-middle (MITM) attacks. MITM attacks are hard to do (he must intercept all packets both ways by taking over a router or poisoning ARP caches), so he would really be a serious attacker.  I am not clear how much (or if any) of that is going on today (in the future there will surely be more, can't predict when...).

In the next level of stunnel setup joe's side verifies the helpdesk.server.com identity. With the CAfile = ... and verify = 2 lines just like you have on joe's side above.  You can (and probably should) delete the " -----BEGIN RSA PRIVATE KEY-----" section from joe's pem file (why give joe helpdesk's private key?)

This will prevent MITM attack, **ASSUMING** the MITM doesn't alter your application as joe downloads it.  If he does that, all bets are off, because now he can make joe run any command he likes.

The highest level of stunnel setup will have helpdesk verify joe's identity as well.  This would require CAfile = and verify = 2 in helpdesk's config and a cert = in joe's.   Normally joe's cert+key would be different from helpdesk's.  Perhaps you want a generic "user" cert+key that comes with the application.  I'm not sure what you really want to do. Which verification is more important to you?

Anyway, there you have it all and you can now do just about anything.

---

### Post by bradleyd on 2007-03-09
sorry, one more thing.
I switched machine to try succes there. All is well except for x11vnc -connect localhost:5500 -rfbport 0 -nopw errors out with Error: could not obtain listening port.

These 2 machines are on same lan. Alls I did was take stunnel and stunnel.cfg and stunnel.conf and put them on the correct machines. stunnel loads fine with .pem file.
anyhelp again would be greatly appreciated.

---

### Post by krunge on 2007-03-09
Hi again,

> All is well except for x11vnc -connect localhost:5500 -rfbport 0 -nopw errors out with Error: could not obtain listening port.

I vaguely remember it was not too long ago I fixed "-rfbport 0" to work properly (i.e. to not try to listen on a TCP port at all).  So the version of x11vnc may be too old for "-rfbport 0" to do the right thing.  So I guess you should not use it in this case, thereby letting it autoprobe an open port.  Probably best to supply "-localhost" in this case.

IMHO, your app should bundle stunnel and x11vnc binaries with it, both suitably built (by you) for best compatibility with the various linux distros and versions you need to support.  I gave some hints WRT static linking libssl, etc.  Let me know if you need more info.

---

### Post by bradleyd on 2007-03-09
you tha man!I was pulling my hair out trying to figure out was has changed. I didn't get much further after our last post(had a tape failure at real job)I was starting to rewrite the application and hit a brick-wall. I had to link libssl on one machine running sarge to get stunnel to work.(like you said)How did you build x11vnc binary?I understand stunnel build. I want you to know most people would have stopped responding after the first few hundred posts. Thanks for sticking in there with me. 
I will be the remote-support king eventualy.lol

---

### Post by krunge on 2007-03-10
> I had to link libssl on one machine running sarge to get stunnel to work. (like you said) How did you build x11vnc binary? I understand stunnel build.

I'm not sure exactly what you want.. but I'll describe static linking libssl.a and libcrypto.a into x11vnc.

I recommend downloading the x11vnc-0.8.4.tar.gz tarball from sourceforge: [http://sourceforge.net/projects/libvncserver]("http://sourceforge.net/projects/libvncserver")

Untar it and then cd to x11vnc-0.8.4, and do the standard thing:

```
./configure
make
```

The binary:  ./x11vnc/x11vnc should be usable as is, but it has dynamic dependency on libssl.so and libcrypto.so, and so the chances of it breaking under general Linux deployment is quite high.  

You can use ldd(1) to list the dynamic dependencies:

```
 ldd ./x11vnc/x11vnc
        linux-gate.so.1 =>  (0xffffe000)
        libssl.so.0.9.7 => /usr/lib/libssl.so.0.9.7 (0xb7f97000)
        libcrypto.so.0.9.7 => /usr/lib/libcrypto.so.0.9.7 (0xb7ea3000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0xb7e71000)
        libXtst.so.6 => /usr/X11R6/lib/libXtst.so.6 (0xb7e6b000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb7e5d000)
        libXinerama.so.1 => /usr/X11R6/lib/libXinerama.so.1 (0xb7e5a000)
        libXrandr.so.2 => /usr/X11R6/lib/libXrandr.so.2 (0xb7e56000)
        libXfixes.so.3 => /usr/X11R6/lib/libXfixes.so.3 (0xb7e50000)
        libXdamage.so.1 => /usr/X11R6/lib/libXdamage.so.1 (0xb7e4d000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb7d51000)
        libnsl.so.1 => /lib/libnsl.so.1 (0xb7d3c000)
        libpthread.so.0 => /lib/tls/libpthread.so.0 (0xb7d2a000)
        libz.so.1 => /lib/libz.so.1 (0xb7d19000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7cf9000)
        libc.so.6 => /lib/tls/libc.so.6 (0xb7be0000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7bdc000)
        libXrender.so.1 => /usr/X11R6/lib/libXrender.so.1 (0xb7bd4000)
        /lib/ld-linux.so.2 (0xb7fea000)
```

To statically link libssl and libcrypto (the other libraries and versions are pretty standard and Linux distros usually don't break them), note that the final link is done in the ./x11vnc subdirectory.  The link line is very long, but one can see it has "-lssl" and "-lcrypto" that we change to "/usr/lib/libssl.a" and "/usr/lib/libcrypto.a" respectively.  So I did this:

```
cd x11vnc
gcc -I .. -g -O2   -o x11vnc  x11vnc-8to24.o x11vnc-cleanup.o x11vnc-connections.o x11vnc-cursor.o x11vnc-gui.o x11vnc-help.o x11vnc-inet.o x11vnc-keyboard.o x11vnc-linuxfb.o x11vnc-macosx.o x11vnc-macosxCG.o x11vnc-macosxCGP.o x11vnc-macosxCGS.o x11vnc-options.o x11vnc-pm.o x11vnc-pointer.o x11vnc-rates.o x11vnc-remote.o x11vnc-scan.o x11vnc-screen.o x11vnc-selection.o x11vnc-solid.o x11vnc-sslcmds.o x11vnc-sslhelper.o x11vnc-uinput.o x11vnc-unixpw.o x11vnc-user.o x11vnc-userinput.o x11vnc-util.o x11vnc-v4l.o x11vnc-win_utils.o x11vnc-x11vnc.o x11vnc-x11vnc_defs.o x11vnc-xdamage.o x11vnc-xevents.o x11vnc-xinerama.o x11vnc-xkb_bell.o x11vnc-xrandr.o x11vnc-xrecord.o x11vnc-xwrappers.o ../libvncserver/libvncserver.a ../libvncclient/libvncclient.a  /usr/lib/libssl.a /usr/lib/libcrypto.a -lcrypt  -L/usr/X11/lib -lXtst -lXtst -lXtst  -lXext -lXinerama -lXrandr -lXfixes -lXdamage -lX11   -lnsl -lpthread -lz -ljpeg
```

and here is the ldd:

```
ldd ./x11vnc
        linux-gate.so.1 =>  (0xffffe000)
        libcrypt.so.1 => /lib/libcrypt.so.1 (0xb7f95000)
        libXtst.so.6 => /usr/X11R6/lib/libXtst.so.6 (0xb7f8e000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0xb7f80000)
        libXinerama.so.1 => /usr/X11R6/lib/libXinerama.so.1 (0xb7f7d000)
        libXrandr.so.2 => /usr/X11R6/lib/libXrandr.so.2 (0xb7f79000)
        libXfixes.so.3 => /usr/X11R6/lib/libXfixes.so.3 (0xb7f74000)
        libXdamage.so.1 => /usr/X11R6/lib/libXdamage.so.1 (0xb7f71000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0xb7e74000)
        libnsl.so.1 => /lib/libnsl.so.1 (0xb7e5f000)
        libpthread.so.0 => /lib/tls/libpthread.so.0 (0xb7e4d000)
        libz.so.1 => /lib/libz.so.1 (0xb7e3c000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0xb7e1d000)
        libc.so.6 => /lib/tls/libc.so.6 (0xb7d04000)
        libXrender.so.1 => /usr/X11R6/lib/libXrender.so.1 (0xb7cfb000)
        libdl.so.2 => /lib/libdl.so.2 (0xb7cf7000)
        /lib/ld-linux.so.2 (0xb7fea000)
```

I hope that makes sense.  One can do this for any libraries that a Linux distro breaks you on for general deployment.  One should **not** do this for core libraries like libc.so.6 or libX11.so.6, however, since they usually need to be matched to the runtime (not build time) system.

For best deployment, you probably want to build the binaries (x11vnc and stunnel) as above on a relatively older distro, say 1-3 years old.  This is mainly to avoid spurious dependencies on new glibc internal interfaces (e.g.  __strncpy_chk()).  Your choice of Sarge sounds reasonable.

If you don't like the link line editing, I think you could make a directory /tmp/libs, copy the libssl.a and libcrypto.a there, and set the environment variable LDFLAGS=-L/tmp/libs before configuring and making.  I didn't test this though.

---

### Post by bradleyd on 2007-03-10
all went well for x11vnc except when I execute it on a sarge box I get libXinerama and libXfixes error.

---

### Post by krunge on 2007-03-11
> all went well for x11vnc except when I execute it on a sarge box I get libXinerama and libXfixes error.

Yes, having the binary go back to Sarge (XFree86 based, vs. Xorg based) is probably asking too much.  On which distro and version did you build the binary?   It is probably better to _build_ it on Sarge (using the libssl.a instructions) and deploy that.  This will move forward better and only lose a few minor features not important for helpdesk mode.

Although if you want to try an experiment, try statically linking libXinerama, libXfixes and libXdamage on the newer distro, perhaps this way:

```
mkdir /tmp/libs
cp /usr/lib/libssl.a /usr/lib/libcrypto.a /tmp/libs
cp /usr/X11R6/lib/libXinerama.a /usr/X11R6/lib/libXfixes.a /usr/X11R6/lib/libXdamage.a /tmp/libs
(cd to the x11vnc-0.8.4 source directory)
env LDFLAGS=-L/tmp/libs ./configure
make
```

I'm curious how this would work out running that binary on Sarge. If you try that let me know if it worked or not.

---

### Post by bradleyd on 2007-03-11
ok, I built x11vnc on a dapper machine. Following your instructions.
After I installed the correct dev packages. libXinerama.a and libXfixes.a and libXdamage.a were under /usr/lib not  /usr/X11R6/lib. No big deal just documenting the steps. 
```
mkdir /tmp/libs
cp /usr/lib/libssl.a /usr/lib/libcrypto.a /tmp/libs
cp /usr/X11R6/lib/libXinerama.a /usr/X11R6/lib/libXfixes.a /usr/X11R6/lib/libXdamage.a /tmp/libs
(cd to the x11vnc-0.8.4 source directory)
env LDFLAGS=-L/tmp/libs ./configure
make
```
then copied the binary to sarge machine. here is the ldd of new x11vnc on sarge.
```
debian2:~# ldd x11vnc
        libcrypt.so.1 => /lib/libcrypt.so.1 (0x4001d000)
        libXtst.so.6 => /usr/X11R6/lib/libXtst.so.6 (0x4004a000)
        libXext.so.6 => /usr/X11R6/lib/libXext.so.6 (0x4004f000)
        libXrandr.so.2 => /usr/X11R6/lib/libXrandr.so.2 (0x4005e000)
        libX11.so.6 => /usr/X11R6/lib/libX11.so.6 (0x40062000)
        libnsl.so.1 => /lib/libnsl.so.1 (0x40129000)
        libpthread.so.0 => /lib/libpthread.so.0 (0x4013e000)
        libz.so.1 => /usr/lib/libz.so.1 (0x4018f000)
        libjpeg.so.62 => /usr/lib/libjpeg.so.62 (0x401a1000)
        libc.so.6 => /lib/libc.so.6 (0x401c0000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0x402f3000)
        libdl.so.2 => /lib/libdl.so.2 (0x402fb000)
        /lib/ld-linux.so.2 => /lib/ld-linux.so.2 (0x40000000)

```
executed it and it starts fine. No errors.
This may be a dumb question, I thought I was going to copy the libraries(/tmp/libs) over to sarge machine so x11vnc could execute(since x11vnc requires them)?
Did I not soft link those libs to /tmp/libs?

---

### Post by krunge on 2007-03-11
> After I installed the correct dev packages. libXinerama.a and libXfixes.a and libXdamage.a were under /usr/lib not /usr/X11R6/lib.

Ah, yes, all part of the "grand plan" to move everything to /usr/lib and /usr/bin.  I personally don't like it...

> This may be a dumb question, I thought I was going to copy the libraries(/tmp/libs) over to sarge machine so x11vnc could execute(since x11vnc requires them)?

No, this is the nifty part of the trick we are doing.  We **statically** link in the lib*.a's instead of **dynamically** linking to the lib*.so's.  Because we cannot guarantee the Linux distros the binary is to be delivered to has the lib*.so's we "bolt on" to the x11vnc binary the parts of the libraries we need.  So x11vnc carries along with it the parts of the libXfixes... libraries needed.

Note that what you did works even though the Sarge X server does not support XFIXES, XDAMAGE, etc extensions.  x11vnc has these libraries statically linked in, but it also queries the X server to see if the extension is supported.  If not (i.e. on Sarge) the x11vnc binary doesn't use those features, but if it does (Dapper) it does.  For example, XFIXES allows it to draw the mouse cursor shape correctly.

---

### Post by bradleyd on 2007-03-12
Thanks. I am going to test binary on sarge machine tonight to see if there is any noticable difference without Xfixes and Xdamage. I at least thought I was going to have to link libssl.0.9.7 to libssl.0.9.8, bu tall worked like you said. Have you noticed any performance hit passing vnc through stunnel?

---

### Post by krunge on 2007-03-12
> Have you noticed any performance hit passing vnc through stunnel?

Nope.  Not even with a 333MHz machine.

---

### Post by bradleyd on 2007-03-28
update:
Everything is working great, I had a problem on a RHEL 5 box with stunnel. I guess I will have to try to build another version of stunnel(I am currently using the one in your ssvnc package)
Thanks again for all your help.

---

### Post by fakie_flip on 2007-05-20
I know that reverse connections can be done with x11vnc, so that if the computer is behind a server, a connection can still be made, but what about ssh. Does anyone know how to do a reverse connection with ssh and how can it be done?

---

### Post by krunge on 2007-05-21
> I know that reverse connections can be done with x11vnc, so that if the computer is behind a server, a connection can still be made, but what about ssh. Does anyone know how to do a reverse connection with ssh and how can it be done?

I'm not exactly sure what you want to do.  Does the ssh originate from the x11vnc side or from the VNC viewer side?  This will make a difference between using "-L port:host:.port" or "-R port:host:.port" for the ssh.

Do you still want the VNC viewer to be in "listen" mode?  Or are you using "reverse" not in the "reverse VNC connection" sense? This will affect the port numbers (e.g. 5500 for listen mode vs. 5900 for normal connection).

Please give more details WRT the hosts involved, the direction you want the ssh to go, any firewalls or NAT routers involved, etc.

---

