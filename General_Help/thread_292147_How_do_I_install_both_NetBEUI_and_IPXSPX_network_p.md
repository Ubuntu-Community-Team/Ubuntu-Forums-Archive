---
title: "How do I install both NetBEUI and IPX/SPX network protocols?"
date: 2006-11-03
forum: General Help
---

### Post by void1 on 2006-11-03
Hello and thanks for the help. I'm a newbie to Kubuntu Edgy.

How do I install both NetBEUI and IPX/SPX network protocols?

I don't find them listed in the package manager ("Adept Manager") nor have I found anything useful in the help pages.

I'd appreciate guidance or pointers to an install guide.

Also, the screen for sharing (Kubuntu->System Settings->Sharing->File Sharing) will not active (Administor Mode...), and the first two lines of text are chopped either on the top or bottom of each character. So I assume there is a bug is the sharing GUI. How do I work around this bug to setup Samba?

Thanks for the help.

---

### Post by ciscosurfer on 2006-11-03
Why do you want to use IPX/SPX?  It is an antiquated and sorely outdated protocol stack.  Use TCP/IP and just make sure the ports you want closed, stay closed (security issues).

Are you connecting to a Novell Netware network?

While IPX/SPX is generally faster on LANs, the overall popularity of TCP/IP has effectively trumped IPX/SPX due to its use on WANs (read: Internet, etc.)  TCP/IP is a more mature protocol and even Netware comes bundled with it now.

Apparently, IPX/SPX has some other benefits in regards to VPNs -- you can use it to sidestep a VPN that forces all TCP/IP traffic to traverse the VPN, preventing any access to local resources such as printers and shared disks.

Instead of NetBEUI, which is unroutable (okay on small- to medium-sized networks that don't need to go out on the Internet, I guess using it is fine -- but still it's antiquated as well -- DNS makes more sense), use NetBIOS-over-TCP/IP, which effectively encapsulates NetBEUI and makes it routable.

Otherwise, [perhaps this will help you]("http://tldp.org/HOWTO/Intranet-Server-HOWTO-4.html").

And [this might help]("http://us2.samba.org/samba/docs/man/Samba-HOWTO-Collection/NetworkBrowsing.html#id2551082") for information on network browsing.

Other Samba resources [available here on the forums]("http://ubuntuforums.org/search.php?searchid=9459444").

---

### Post by void1 on 2006-11-03
"Why do you want to use IPX/SPX?"

For added security, the windows machines use IPX (or NetBeui) on the LAN (see: [http://www.grc.com/su-rebinding9x.htm)](http://www.grc.com/su-rebinding9x.htm)).  

Where are the Kubuntu packages for NetBeui and IPX?

"Other Samba resources available here on the forums." <- link is broken

---

### Post by void1 on 2006-11-03
For other newbies, I've found an *EXCELLENT* guide to installing Samba on a peer-to-peer network with Windows computers.  It is: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Now I still need to install NetBEUI and IPX.  If anyone can provide pointers to a guide, I'd appreciate it.](*,) 

Good luck.

---

### Post by dcstar on 2006-11-04
> **void1 said:**
> "Why do you want to use IPX/SPX?"

For added security, the windows machines use IPX (or NetBeui) on the LAN (see: [http://www.grc.com/su-rebinding9x.htm](http://www.grc.com/su-rebinding9x.htm)).  


And you are aware that this specific article refers to Windows 95 and 98 only, and that the only other article that recommends using these protocols is for NT4?

If you are using those antiquated Microsoft O/S's, then most of the current vulnerabilities around won't even work on things that old, so the "protection" you'd get from implementing them seems fairly pointless.

---

### Post by ciscosurfer on 2006-11-05
You could always write/code a new protocol (suite) to suit your needs. :lol:\\:D/

---

### Post by Prof.Arronax on 2007-03-08
(No quote here; observation only)

I too want to enable NetBEUI on my Ubuntu Edgy machine; I see a section that mentions the protocol in the protocol listings.  But all the answers I've seen in these forums have been in a non-helpful, negative or condescending tone.  Disappointing attitude. :confused:

I'm going to keep searching; someone more knowledgable will surely have something helpful.  When I find that I'll import that post here.

---

### Post by cdheer on 2007-05-04
So is there a way to use either NetBEUI or IPX/SPX for file/print sharing on Ubuntu?  Most of the replies I've seen have been of the unhelpful why-would-you-want-to variety instead of actually commenting on whether it's possible or not.

--chris

---

### Post by Prof.Arronax on 2007-05-04
> **cdheer said:**
> So is there a way to use either NetBEUI or IPX/SPX for file/print sharing on Ubuntu?  Most of the replies I've seen have been of the unhelpful why-would-you-want-to variety instead of actually commenting on whether it's possible or not.

--chris
Greetings.

Well, Chris, as you can see, the folks that purportedly know something in these forums are, shall we say, substantially less than helpful.  I've just about given up on these "forums" for just that reason.  Techno-snobs that talk down to you.  Utterly useless.  :mad:

---

### Post by DoktorSeven on 2007-05-04
To directly answer your question, networking protocols are enabled in the kernel configuration.  The default (K)Ubuntu kernel should have both enabled as at least a module, which means that they should work when needed.

The GUI you referred to, I couldn't find by the path you gave; there was a "File Sharing" component under the "Internet and Network" section that did bring up a dialog with the bottom cut off, but a simple resize of the window fixed that.

Can you give a few more details, including what you're trying to accomplish?

---

### Post by cdheer on 2007-07-05
Not sure what the original poster was referring to, but I merely want to get file sharing (and, in a perfect world, printer sharing) to work (Samba would be best) using a non-IP protocol.  My work laptop has a VPN client that kills my local IP connectivity.  When I used to use XP for my server, I would simply have it run IPX/SPX or NetBEUI and I could still reach it.  I want to do the same thing with my Ubuntu server.

---

### Post by cdheer on 2007-09-29
Well in case anyone cares, I never did get either IPX/SPX or NetBEUI working.  However, I found an alternative that, while hardly optimal, works: Appletalk.  Get netatalk up and running on your Ubuntu box (pretty straightforward) and then google for PC Maclan.  You can find a demo that works for 3 hrs at a time.  As near as I can tell there's no legitimate way to purchase PC Maclan anymore, nor do there seem to be alternatives.

Set up your SMB shares to also be AFP shares, and then you can use PC Maclan to get file access.  Should work with printers too, although I don't use that.

Tip: make sure your Appletalk Shares are named differently from your SMB shares.  Why?  As near as I can figure, PC Maclan sits as some kind of shim between Appletalk/AFP and Windows' SMB logic.  PC Maclan seems to present the shares to Windows as SMB shares.

So for example, if you have a server named "MYSERVER" and a Samba share named "Users," then from Windows normally that's \\MYSERVER\Users.  That works fine without the VPN up, but now let's say you fire up your VPN connection.  You then use PC Maclan to browse your Appletalk network, and you see a server named Myserver and you connect to it.  So far so good...and then you try to access the AFP share named Users.  XP will come back and say "\\MYSERVER\Users" is not available...because XP knows there's an SMB server/share combo with that name, so it tries to access it directly via SMB.

At least, that's what happened to me.  I just renamed my "Users" share under netatalk to "AFP Users" and all was well.

File/folder browsing is very slow.  I have no idea why -- possibly an Appletalk thing, though more likely a PC Maclan thing.  Actual file copying/accessing seems good enough, however.

Like I said, not optimal -- I'd rather have Ubuntu doing SMB over IPX or NetBEUI, but I was unable to really get that going.

---

### Post by RiTarDid on 2008-02-04
i agree on the non-helpful replies mentioned earlier, but I can understand it.  If you want advice the "techno-snobs" need to know a little more about what your doing so they don't just advise you to do it differently.  They're trying to look out for your system by advising against using outdated protocols.....

As for me, I'm trying to run the 10-year-old classic "Starcraft" under wine and require the IPX protocol to join a LAN game....I understand the module must be installed in the kernel and assume from what i've read so far that it should already be in the current kernel.  I have done 'sudo apt-get install ipx' with no problem, added 'ipx' to my /etc/modules file and rebooted.  i have no errors so i assume it worked but i don't know how to check if ipx is actually loading into the kernel. In starcraft it simpy "cannot find a network provider" when i try to launch an ipx game.

---

