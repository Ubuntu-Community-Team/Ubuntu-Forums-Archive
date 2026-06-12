---
title: "[SOLVED] Firefox Add-ons Won't Install"
date: 2007-10-22
forum: General Help
---

### Post by Glunn11 on 2007-10-22
Hello Ubuntu community!
I have been reading other threads about Firefox add-ons not working in Gutsy Gibbon, and none have been able to solve my problem. When I click on a link to download an add-on, nothing pops up. I do wait for about 2 minutes, and still nothing pops up. I have checked the Add-ons section, and nothing is in the Install queue, either.
I have tried uninstalling and reinstalling Firefox, as well as following some instructions on deleting and starting up a new, fresh profile. Neither have helped. I did not have this problem on Feisty Fawn.
HELP! Thanks.

-Glen

---

### Post by terminateprocess on 2007-10-22
The same thing happened to me, and I still have no idea why this happens. I believe it is somehow linked to the new UbuntuFox package management thing for extensions. There's probably an obvious and graceful solution for this, but I haven't seen it yet. Here's how I got around this:

First, get the URL for the extension you want. I did this by right clicking on the "Download extension" button on the web page for each extension, and then clicking "Copy Link Location".

Next, open a terminal and run
```
wget --no-check-certificate (pasted URL)
```
in some temporary directory.

Finally, open up the directory you just downloaded the *.xpi file to in Nautilus. Then, drag and drop the file over the Firefox window. Firefox should pop up the usual installation dialog. For some reason, it seems like it can install them just fine, but just can't download them for some strange reason. If anybody has an idea why this is, please enlighten us.

---

### Post by Glunn11 on 2007-10-23
Thank you for your prompt response, terminateprocess!
However, the terminal cannot connect to releases.mozilla.org.

Here's the lowdown:
glen@glen-desktop:~$ wget --no-check-certificate [https://addons.mozilla.org/en-US/firefox/downloads/file/19977/halloween-2.2-fx.jar](https://addons.mozilla.org/en-US/firefox/downloads/file/19977/halloween-2.2-fx.jar)
--15:46:42--  [https://addons.mozilla.org/en-US/firefox/downloads/file/19977/halloween-2.2-fx.jar](https://addons.mozilla.org/en-US/firefox/downloads/file/19977/halloween-2.2-fx.jar)
           => `halloween-2.2-fx.jar'
Resolving addons.mozilla.org... 63.245.209.31
Connecting to addons.mozilla.org|63.245.209.31|:443... connected.
WARNING: Certificate verification error for addons.mozilla.org: self signed certificate in certificate chain
HTTP request sent, awaiting response... 302 Found
Location: [http://releases.mozilla.org/pub/mozilla.org/addons/1360/halloween-2.2-fx.jar](http://releases.mozilla.org/pub/mozilla.org/addons/1360/halloween-2.2-fx.jar) [following]
--15:46:43--  [http://releases.mozilla.org/pub/mozilla.org/addons/1360/halloween-2.2-fx.jar](http://releases.mozilla.org/pub/mozilla.org/addons/1360/halloween-2.2-fx.jar)
           => `halloween-2.2-fx.jar'
Resolving releases.mozilla.org... 32.1.4.248
Connecting to releases.mozilla.org|32.1.4.248|:80... 

And it will not proceed from there after a rather long wait.

---

### Post by trmanco on 2007-10-23
Same here...
Been tring to solve this for about 3 days and nothing yet

---

### Post by por100pre1 on 2007-10-23
Many popular add-ons for Firefox are available in Gutsy's Add/Remove. Search Firefox in Add/Remove and you'll find them. :)

---

### Post by rudeboyskunk on 2007-10-23
This might sound silly, and possibly not be the case, but do you have your pop-up blocker enabled?  It might be keeping the correct window from opening up...?

What I usually do is just download the extensions into /home/*username*, and then manually installing them.

---

### Post by Glunn11 on 2007-10-23
The pop-up blocker isn't the issue (just turned it off and tried - still nothing). Based on what I found in the terminal, my computer won't connect to the needed website to get the extensions and themes I want.

---

### Post by jusmurph on 2007-10-23
I just downloaded (they came this morning) a Firefox update that mentioned something about firefox plugins.

Have you updated firefox?

---

### Post by Glunn11 on 2007-10-23
I also downloaded the update with the Update Manager pop-up - it did not solve my issue.

---

### Post by jayaramk on 2007-10-23
even it neither worked for me tooo..... i need to install firefox addon's from the mozilla page... but i can't ... can i have a solution for it/?

---

### Post by trmanco on 2007-10-24
> **rudeboyskunk said:**
> This might sound silly, and possibly not be the case, but do you have your pop-up blocker enabled?  It might be keeping the correct window from opening up...?

What I usually do is just download the extensions into /home/*username*, and then manually installing them.

```
trmanco@trmanco-desktop:~$ wget --no-check-certificate https://addons.mozilla.org/en-US/firefox/downloads/file/17688/alexa_sparky-1.1-fx.xpi
--15:21:52--  https://addons.mozilla.org/en-US/firefox/downloads/file/17688/alexa_sparky-1.1-fx.xpi
           => `alexa_sparky-1.1-fx.xpi'
Resolving addons.mozilla.org... 63.245.209.31
Connecting to addons.mozilla.org|63.245.209.31|:443... connected.
WARNING: Certificate verification error for addons.mozilla.org: self signed certificate in certificate chain
HTTP request sent, awaiting response... 302 Found
Location: http://releases.mozilla.org/pub/mozilla.org/addons/5362/alexa_sparky-1.1-fx.xpi [following]
--15:21:53--  http://releases.mozilla.org/pub/mozilla.org/addons/5362/alexa_sparky-1.1-fx.xpi
           => `alexa_sparky-1.1-fx.xpi'
Resolving releases.mozilla.org... 32.1.4.248, 2001:4f8:0:2::1f
Connecting to releases.mozilla.org|32.1.4.248|:80... failed: Connection timed out.
Connecting to releases.mozilla.org|2001:4f8:0:2::1f|:80... failed: Network is unreachable.
```

Getting the same thing here...

---

### Post by cytg on 2007-10-24
sitting ducks without noscript .. ill problary hold off gutsy till you guys figure it out :)

---

### Post by vyvee on 2007-10-24
Goodness... I installed Gutsy on two computers. One works fine with add-ons... for another I encounter exactly the same problem!
I use wget to get the add-ons manually... also failed... help...

---

### Post by vyvee on 2007-10-24
After 3 days I've finally found the cause & **SOLVED the problem**!! :) :guitar:

[SIZE="3"]**Workaround**[/SIZE]

Edit /etc/hosts, and add the following line somewhere...
```
64.50.236.214   releases.mozilla.org
```

(Or some other valid & 'working' IP... see below)

Try again (even don't need to restart firefox), and it just works!

[SIZE="3"]**Cause**[/SIZE]

Sometimes, or for certain IP range, or... ??  the DNS server returns me 32.1.4.248 for releases.mozilla.org, and the server at this address seems not working. (Hi trmanco, I see that you have exactly the same problem as I faced!)  In particular, I get
```

$ host releases.mozilla.org
releases.mozilla.org has address 32.1.4.248
;; Warning: Message parser reports malformed message packet.
;; connection timed out; no servers could be reached
```

Then I try it on another computer at another location that works, I get:
```

$ host releases.mozilla.org
releases.mozilla.org has address 207.200.66.54
releases.mozilla.org has address 64.12.204.21
releases.mozilla.org has address 64.50.236.52
releases.mozilla.org has address 64.50.236.214
releases.mozilla.org has address 64.50.238.52
releases.mozilla.org has address 156.56.247.196
releases.mozilla.org has address 204.152.184.113
releases.mozilla.org has IPv6 address 2001:4f8:0:2::1f
```

But... why??  Something related to that firefox server?  I stay in malaysia, and both computers are accessing internet using the same server provider (streamyx), with exactly the same DNS settings... how about others who have this problem?

---

### Post by Glunn11 on 2007-10-25
Thank you, vyvee! That did solve my problem, and apparently it will solve many others. Sticky, perhaps?
SOLVED!

---

### Post by Kappity on 2007-10-25
Solved my problem for installing a theme in Firefox.   Two questions, if anybody's interested.

Could defining a specific host like this for Firefox downloads be a security risk in any way?

Was this problem in Feisty, too, or did it come with the upgrade to Gutsy?  I don't know, because I don't think I'd tried to add any add-ons or themes before I did the upgrade.

---

### Post by vyvee on 2007-10-25
Defining a host like this avoids querying the DNS for the latest IP address of releases.mozilla.org. Personally I think it poses a security risk only when Firefox someday abandons this public IP address later, AND the IP address falls on the hands of some crackers. The possibility is there, but I believe that it's small. Anyway, once a while you may want to comment the line out, and do a 'host releases.mozilla.org' to check if the problem is still there.

Hmm... I still have a laptop with Ubuntu 7.04 Feisty Fawn. I will check later if the problem is there & post the results here.

---

### Post by vyvee on 2007-10-26
I have just tested the IP issue again on both Gutsy Gibbon and Feisty Fawn. Two computers installed with these two versions are connected to the same router, which is in turn connected to a D-Link ADSL Dial-up Modem. I think the setup should be simple & won't result in some subtle problems.

Then I tested it with **Gutsy Gibbon**:
```

$ host releases.mozilla.org
releases.mozilla.org has address 204.152.184.113
releases.mozilla.org has address 207.200.66.54
releases.mozilla.org has address 64.12.204.21
releases.mozilla.org has address 64.50.236.52
releases.mozilla.org has address 64.50.236.214
releases.mozilla.org has address 64.50.238.52
releases.mozilla.org has address 156.56.247.196
;; Warning: Message parser reports malformed message packet.
*(After about 10 seconds)*
;; connection timed out; no servers could be reached
$

```

And try again:
```

$ host releases.mozilla.org
releases.mozilla.org has address 204.152.184.113
;; Warning: Message parser reports malformed message packet.
;; connection timed out; no servers could be reached
*(After about 10 seconds)*
;; connection timed out; no servers could be reached
$

```

Tough. Not the problematic IP 32.1.4.248 32 this time! Then I try it again on the SAME computer:
```

$ host releases.mozilla.org
releases.mozilla.org has address 32.1.4.248
;; Warning: Message parser reports malformed message packet.
*(After about 10 seconds)*
;; connection timed out; no servers could be reached
$

```

What?! Then I try it on another computer installed with **Feisty Fawn**:
```

$ host releases.mozilla.org
releases.mozilla.org has address 32.1.4.248
;; Warning: Message parser reports malformed message packet.
*(After about 10 seconds)*
;; connection timed out; no servers could be reached
$

```

Then I tested it on another computer installed with Windows XP.  I use 'ping releases.mozilla.org' to check the IP address, and 'ipconfig /flushdns' to flush the cache. (What's the equivalence of 'host' in Windows? Sorry I'm not really a Windows guy...) I observed similar behavior.

So the problem is not new to Gutsy Gibbon, and is probably OS-independent & not related to GNU/Linux at all. My guess is, it looks like a Gutsy Gibbon problem because this weird problem did happen a few months ago when we just installed Feisty Fawn, and 'unfortunately' it happened not long before the release of Gutsy Gibbon.

So what exactly the problem is? Some DNS inconsistency problem? I don't have much idea at the moment... anybody?

---

### Post by ptdelfim on 2007-10-27
I had the same problem also. It is related with IPv6 being activated by default.

I simplest solution is to type "about:config" in the address bar, filter by "ipv6" and change "network.dns.disableIPv6" to true.

:)

---

### Post by scaglifr on 2007-10-27
Different variant of the problem here.  Add-on downloads fine, the "install" button counts down from 3 and then becomes un-greyed, click install, the extension then downloads fine  and then a pop-up appears reporting "Unexpected installation error check error log - 203 ".

Am trying to migrate from SuSE and this Firefox ( and for that matter Flock ) issue is a real pain.

---

### Post by fatallyhuman on 2007-12-16
This is not an Ubuntu specific problem. In fact, Ubuntu has never given me trouble with this. I first noticed this issue with Mandriva 2008, and now I'm running across it again on Debian Sid. I fixed it like ptdelfim said by disabling ipv6 in Firefox. I had to restart Firefox for the new setting to take effect though.

---

