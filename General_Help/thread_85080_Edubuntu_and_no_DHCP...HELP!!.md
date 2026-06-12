---
title: "Edubuntu and no DHCP...HELP!!"
date: 2005-11-01
forum: General Help
---

### Post by badboyz107 on 2005-11-01
Hey all I have just recently installed edubutu to give it a test drive thinking I might put it on my daughters computer and get rid of windoz....HOWEVER...

As I did the install it asked for the IP addy that I wanted this machine on...confused me since Breezy offers dhcp during install SO I skipped that step thinking I could do DHCP after the install

NOW I cant get to the System -> Administration -> Networking because the networking is grayed out.  The hard ware does reflect the device and all that so what the hell did I do to it???  

Suggestions on how to resolve this issue????

---

### Post by Kyral on 2005-11-01
Hmm, can you give me the output from

```
ifconfig
```

---

### Post by badboyz107 on 2005-11-01
Okay...pardon my stupidness but do I get this text by just typing in the

ifconfig

Or do I need to do something else in addition?  When I typed it in just ifconfig it just went right back to the prompt and doesnt do anything at all...if I gedit ifconfig it gives me a blank text doc

---

### Post by Kyral on 2005-11-01
in the Terminal type ifconfig and paste whatever it spits out (even include the prompt with command if it spits out nothing)

---

### Post by badboyz107 on 2005-11-01
okay here is what happens...

troy@ubuntu:~$ ifconfig
troy@ubuntu:~$ 


So like I said it doesnt seem to do anything at all with that command??  ](*,) :x 
the networking is still grayed out so doesnt do anything when I go to it.....what now???

---

### Post by Kyral on 2005-11-01
Hm...

Can you paste the output from lspci?

I know this is being fustrating, but I will do everything I can to help you :D

---

### Post by dbott67 on 2005-11-01
Try the following:
```
sudo apt-get install dhcp3-client
```
There are a few dependencies that will get tagged along the way (dhcp3-common and a few others).

You could also use Synaptic if you prefer & do a search for **dhcp3-client**.

-Dave

---

### Post by badboyz107 on 2005-11-01
actually I cant paste it because I'm on a seperate machine that doesnt ahve a floppy drive (like the one with ubuntu) but has usb (that the ubuntu doesnt) so I'm kinda shit outa luck....

can you tell me what to look for?  with that command it shows a list of hardware and the revisions, etc etc...

---

### Post by Kyral on 2005-11-01
You want to look for a line that looks like this

0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

Its gonna be slightly different than yours, but look for lines that say "Ethernet Controller"

---

### Post by badboyz107 on 2005-11-01
Okey dokey then here it is

0000:00:11:0 Ethernet controller: 3comm Corporation 3c9058 100 BaseTX [Cyclone] (rev24)

---

### Post by dbott67 on 2005-11-01
What is the output of
```
sudo cat /etc/network/interfaces
```

You can also try the following commands to start your interface from the command line:
```
sudo ifup eth0
sudo dhclient eth0
```

-Dave

---

### Post by badboyz107 on 2005-11-01
[QUOTE=dbott67]What is the output of
```
sudo cat /etc/network/interfaces
```[COLOR="Red"][FONT="Comic Sans MS"]used by ifup(8 ) and ifdown (8 ) see the interfaces(5) manpage[/FONT][/COLOR]

You can also try the following commands to start your interface from the command line:
```
sudo ifup eth0

[FONT="Comic Sans MS"][COLOR="Red"]failed to open statefile /etc/network/run/ifstate: permission denied[/COLOR][/FONT]

sudo dhclient eth0
```[FONT="Comic Sans MS"][COLOR="Red"]site0: unkown address type 776 cant create /var/lib/dhcp3/dhclient.leases: permission denied
cant create /var/run/dhclient.pid 
drop_privileges: could not set group id[/COLOR][/FONT]

---

### Post by badboyz107 on 2005-11-01
Also here is a very dumb question...

I was given the impression that the $ indicated I was a normal user while the # indicates root user....

Why is it when I do these commands using sudo etc.. it tells me this
unable to lookup ubuntu via gethostbyname

but I try the commands WITHOUT sudo and the work fine?  that is just wierd...oh and still no net....boohooo

Im having to handwrite this all out and retype it on my other computer

---

### Post by badboyz107 on 2005-11-02
Oh come on guys....help a guy out thats to stupid to figure it out on his own....lol

---

### Post by dbott67 on 2005-11-02
Okay... this is very strange... something is definitely wrong.  When you type a command such as **cat /etc/network/interfaces** at the command line (without **sudo**), you should get a "permission denied" error (or something to that effect). The sudo in front should give you root permissions.

I think it must be something with Edubuntu's configuration. Unfortunately, I have not tried Edubuntu yet, so I can't offer any further help.

It may just be easier to do a re-install... 2 hours of watching the screen scroll by vs. 3 days of trying all sorts of commands...

(BTW, I'm one of the guys who NEVER likes to say "re-install" --- I always like to figure out the problem, so I can prevent/fix it in the future. But, seeing as it was never working right from the beginning, it may be simpler to start again.)

-Dave

---

### Post by Kyral on 2005-11-02
the command "whoami" should tell you who you are logged in as ;P

The whole "getbyhostname" thing means that your hostname isn't configured right. Uhh, anyone know the dpkg-reconfigure to redo the networksetup?

---

### Post by badboyz107 on 2005-11-02
hummmmm well the "whoami" command just tells me my name...as if I didnt already know it....well most days I do....

I think it is BROKEN and maybe a good reinstall will teach this thing who is boss!  I hate to do that Buuuttttt

---

### Post by badboyz107 on 2005-11-03
Okay no other handy dandy suggestions for my problem?

---

### Post by badboyz107 on 2005-11-07
Okay all just so there is some resolution to this post...

I went ahead and did a re-install since nothing seemed to be working right....when it prompted me for an IP during install I just assigned it one that would be within my DHCP range...the install when smoothly and when I finally got it to boot up the internet worked

THEN I could change the networking settings to accept DHCP....done and done!!!!!    :p

---

