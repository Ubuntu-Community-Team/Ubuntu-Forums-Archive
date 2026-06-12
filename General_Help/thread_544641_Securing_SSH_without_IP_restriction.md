---
title: "Securing SSH without IP restriction"
date: 2007-09-06
forum: General Help
---

### Post by phillips321 on 2007-09-06
Hi guys,

I have a watchguard firewall and notice that i had someone opening and closing connections to ssh (port22).

I guess they were trying to brute-force my ssh password?

what ways can i secure my ssh?

i cannot lock connections down to an IP range because i regularly connect off my mobile of which has a dynamic ip.

is it possible that if an incorrect password was type i can block that ip for n seconds?

what other ways can i secure my ssh?

cheers in advanced guys

P.s. to name and shame the ip was 71.252.176.11 (anyone find any info about this ip)

---

### Post by sonofusion82 on 2007-09-06
Hmm, using GeoIP service, [http://www.maxmind.com/app/locate_ip](http://www.maxmind.com/app/locate_ip)
the IP appears to be from Texas, US

Also, you can disable interactive keyboard login so that they cannot brute force the login, [http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/](http://thinkhole.org/wp/2006/10/30/five-steps-to-a-more-secure-ssh/)

---

### Post by eentonig on 2007-09-06
1.public key authentication.
2. Find out which IP range(s) are used by your mobile service. Most likely that'll be one or two class C's. Which still allows you to block the rest of the world to connect. I only have my companies class B as allowed. Except when I know I'm going to use someone else connection to ssh home. Then I enable the range(s) owned by that provider.
3. Make sure no (default) user except you is allowed ssh acces.
4. Provide a really, really difficult password for your account. (Prefferably, create another account to do the ssh access. And then use su to get to your account.)
5. ...

---

### Post by bam1234567 on 2007-09-06
By the way the coordinantes were 32.9588  -96.9812 and heres where they are (indicated in red). (roughly)[ATTACH]42748[/ATTACH] (Click on it)

---

### Post by HermanAB on 2007-09-06
Brute force attacks against FTP and SSH are going on all the time.  The simple solution is to change those services to non-standard ports like 2121 and 2222 or whatever.  This works very well, because script kiddies are stupid...

The most important thing is to use long passwords with 9 or more characters.  Even just starting your username or password with 'z' increases your security enormously, since the scans always start with 'a' for absolutely retarded.

Cheers,

H.

---

### Post by HermanAB on 2007-09-06
BTW, the better way to protect against brute force attacks is to throttle new connections using iptables.  Google for 'iptables rate limiting'.  There are various complicated schemes that will scan your system logs and drop connections from abusers, but rate limiting is just as effective and much simpler.  

If you rate limit, then an attacker will try only 8 combinations, then give up and go away.  This is due to a fixed timeout limitation in the SSL library, which the script kiddies are too stupid to change.

Cheers,

H.

---

### Post by Warren Watts on 2007-09-06
Here is a thread I posted a month or so ago in regards to SSH security with some of the same questions, along with my solution and suggestions from other posters:
[URL="http://ubuntuforums.org/showthread.php?t=520668"]
http://ubuntuforums.org/showthread.php?t=520668[/URL]

Hope this helps!

---

### Post by cypresstwist on 2007-12-07
Also worth reading: [Tips for a more secure OpenSSH server]("http://www.mylro.org/index.php/2007102698/Articole/How-To/Tips-for-a-more-secure-OpenSSH-server/menu-id-52.html")

---

