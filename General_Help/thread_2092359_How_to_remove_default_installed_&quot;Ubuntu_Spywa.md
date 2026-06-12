---
title: "How to remove default installed &quot;Ubuntu Spyware&quot;"
date: 2012-12-07
forum: General Help
---

### Post by TheForumTroll on 2012-12-07
If you haven't read it then this Free Software Foundation article "[**Ubuntu Spyware: What to Do?**]("http://www.fsf.org/blogs/rms/ubuntu-spyware-what-to-do")" is an interesting and scary read. 

[I][INDENT]"Ubuntu, a widely used and influential GNU/Linux distribution, **has installed surveillance code**. When the user searches her own local files for a string using the Ubuntu desktop, Ubuntu sends that string to one of Canonical's servers. (Canonical is the company that develops Ubuntu.)

This is just like the first surveillance practice I learned about in Windows. My late friend Fravia told me that when he searched for a string in the files of his Windows system, it sent a packet to some server, which was detected by his firewall. Given that first example I paid attention and learned about the propensity of "reputable" proprietary software to be malware. Perhaps it is no coincidence that Ubuntu sends the same information.

Ubuntu uses the information about searches to show the user ads to buy various things from Amazon"[/INDENT][/I]


This makes me think of AOL and Microsoft who also does/did this. The very reason I use Ubuntu is to get away from companies like them and software with this kind of privacy issues.. 



So, how do I get this stuff out of my computer? What packages are involved? I know it can be turned off but its default state is On (*which it clearly shouldn't be*) and I don't want to check it at every update to see if it is back at the default setting.

---

### Post by ageofsteam on 2012-12-07
Do the older versions of Ubuntu have this? Which version started it? I use Narwhale and don't like the idea of people spying on me. :(  It's creepy.

---

### Post by haqking on 2012-12-07
```
sudo apt-get remove unity-lens-shopping
```

---

### Post by vexorian on 2012-12-07
> **ageofsteam said:**
> Do the older versions of Ubuntu have this? Which version started it? I use Narwhale and don't like the idea of people spying on me. :(  It's creepy.
It is a new 12.10 feature and looking at the previews of 13.04, it is only going to get worse in the future.

You can opt-out by typing that command line above. As for me, this is a deal breaker. Once I have to upgrade from 12.04 to something else I Will have to find a fork or try Debian maybe.

I think RMS is right at the end. For a moment I considered to just install 12.10 and remove the feature. But we shouldn't feel comfortable recommending ubuntu anymore. It is not good. Even if I trust Canonical, any security breach of their databases could reveal a log of our desktop searches. I admitted proprietary software being included because many times it is really needed to make ubuntu work at all in a computer. But this crosses the line.

---

### Post by grahammechanical on 2012-12-07
Let us make sure we have facts and not FUD

[http://www.ubuntu.com/aboutus/privacypolicy]("http://www.ubuntu.com/aboutus/privacypolicy")

Regards

---

### Post by snowpine on 2012-12-07
Here is the SABDFL's response for counter-balance:

[http://www.markshuttleworth.com/archives/1182](http://www.markshuttleworth.com/archives/1182)

Of particular note:

> Why are you telling Amazon what I am searching for?

We are not telling Amazon what you are searching for. Your anonymity is preserved because we handle the query on your behalf. Don&#8217;t trust us? Erm, we have root. You do trust us with your data already. You trust us not to screw up on your machine with every update. You trust Debian, and you trust a large swathe of the open source community. And most importantly, you trust us to address it when, being human, we err.

---

### Post by greatsirkain on 2012-12-07
well I ripped out zeitgeist straight away ([why is that even there??]which broke Unity but I use LXDE anyway, loads faster, basic & more user friendly) and geolocation then eventually whoopsie, I had left whoopsie for a while because I figured the crash reports were helping everyone but kworker kept freezing my system just before whoopsie appeared. Then I took out gwibber, thunderbird and all the other unnecessary junk. everything worked fine..

...Until I started pulling gnome stuff then I broke it and had a hard time recovering my encrypted home directory to my fresh Lubuntu install.

I suggest you start by getting LXDE or the Lubuntu core because when you remove zeitgeist the nautilus file manager and unity desktop go with it.

---

### Post by Elfy on 2012-12-07
Closed.

#3 has the method to stop this.

If you want to go over old ground then please find one of the threads in Recurring Discussions.

---

