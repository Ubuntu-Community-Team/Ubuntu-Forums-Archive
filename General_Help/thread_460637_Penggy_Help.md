---
title: "Penggy Help"
date: 2007-05-31
forum: General Help
---

### Post by werewolfzx8 on 2007-05-31
Alright, so I've tried several different ways of getting AOL dial-up working. [It's for a friend who can't get DSL, and her mom thinks AOL is the greatest thing in the world...]

Then stupid me figured out there is a program called Penggy right in the ubuntu package manager.

So I install it and it seems to work, up until the part where it tries to find the modem.

It's an Agere, I can't remember the version or anything. Ubuntu seems to recognize it, and when I type lspci -vv it shows up in the list.

But when I use Penggy it says there is no /dev/modem.

I'm not really sure what I should do next... It looks like the drivers are installed, and even if they're not, I'm still not sure where to get Agere drivers for linux.

:(

---

### Post by tronica on 2007-05-31
can you be more specific on the modem model. I think Agere is made by lucent, but just guessing.

---

### Post by phidia on 2007-05-31
[http://www.linmodems.org/](http://www.linmodems.org/)

Use the above link to download the scanmodem tool and you can use the how to at that site or at the community docs here (check the link in my sig)

---

### Post by phidia on 2007-05-31
> **tronica said:**
>  I think Agere is made by lucent, but just guessing.

I believe that's correct-there were many different models though, which is why the scanmodem tool helps. I had one of these (winmodems) working quite some time ago but an external modem is much easier to set up.

---

### Post by werewolfzx8 on 2007-05-31
Ok I used scanModem and it says she has a Agere systems V.92 56k windmodem.

---

### Post by phidia on 2007-05-31
[http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) Download the latest driver from the preceeding link, unpack it, read the README file to install it.
After you've done that go to the following link to set up the modem.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

---

### Post by werewolfzx8 on 2007-05-31
> **phidia said:**
> [http://www.heby.de/ltmodem](http://www.heby.de/ltmodem) Download the latest driver from the preceeding link, unpack it, read the README file to install it.
After you've done that go to the following link to set up the modem.
[https://help.ubuntu.com/community/DialupModemHowto](https://help.ubuntu.com/community/DialupModemHowto)

Yeah, I managed to figure that out. But I have no clue which one of these to download.
I clicked the link that sent me to the pages with the 2.6 kernel support, but I have no clue which to get.

whats the difference inbetween alk-4, alk-5, etc.

I also went into the Ubuntu directory, and I've seen number similar to numbers like 26b1 when setting up a wireless router.

Do modems have addresses like this? and if so, how could I check?

Sorry to be such a hassle, I'm just completely confused, and tired of trying to set this up by myself.

---

### Post by phidia on 2007-06-01
I don't know if the linmodem site specified but the latest driver would be the one you want IMO.
So the most recent date or the highest release #.

The how to should give you the details on setting up your modem, but I use dial up so if you have specific problems I'll try to help you-probably going to sleep in another 1/2 hour though.

Once the driver is installed. setting up the modem shouldn't be too difficult. There is a configuration script > sudo pppconfig when you run that, from the terminal, it will ask you for the info it needs to set up ppp and related files.

---

### Post by werewolfzx8 on 2007-06-05
Alright, I got her computer at my house found the Agere drivers in the restricted modules, and then put penggy on it. But now I don't know how to set it up. I edited the penggy.cfg file and the aol-secrets, putting in her name and password.

When I try to start it I get an error saying /dev/modem doesn't exist.

So I changed the modem device to ttyS0 and tried it, It goes to the next line but doesn't do anything.

---

### Post by werewolfzx8 on 2007-06-05
Does anybody know how to do this, or at least know how to find out which device it is? [ like /dev/modem, ttyS0, etc]

It doesn't look to hard to figure out. I just know I'm skipping over something that I should be configuring in the penggy.cfg file. :(

---

### Post by werewolfzx8 on 2007-06-06
I'll give it one more try. Anybody?

---

### Post by diablo75 on 2007-07-06
I am having the same problem.

I also noticed this problem when I just run "penggy" at a terminal without sudo:

rick@rick-laptop:/etc/penggy$ penggy
Can't create pid file /var/run/penggy.pid: Permission denied (13).
Unable to open /dev/net/tun: Permission denied(13).
Assuming 2.2 kernel method.
Unable to open a valid tun device (using 2.2 kernel method).
Fatal error, exiting.
Can't remove /var/run/penggy.pid: No such file or directory (2).


When I run it with Sudo, I end up where you've ended up:

rick@rick-laptop:/etc/penggy$ sudo penggy
Can't open device /dev/modem: No such file or directory (2)
Fatal error, exiting.

----------------

I have a HP ZD7000, the modem is an AC '97.  How do I get this to work?

---

