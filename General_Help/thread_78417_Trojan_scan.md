---
title: "Trojan scan"
date: 2005-10-18
forum: General Help
---

### Post by towsonu2003 on 2005-10-18
Hi,
I found this in a news site:
[http://www.linux.com/article.pl?sid=05/10/14/1539210](http://www.linux.com/article.pl?sid=05/10/14/1539210)

It's about scanning trojan-like net activity... Command is lsof (if any of you is familiar). this is the first time I am hearing about trojan in linux (well, okay, I am a newbie :) ). 

I was wondering whether we have a similar tool in ubuntu repositories or should I compile it from source? (Ahh I was very happy with not compiling :) Now i have to read how to convert staff to Debian packages and so on :rolleyes: ;)  ...)

---

### Post by paddyg on 2005-10-18
Perhaps not trojans, what about backdoors, rootkits or other worms?

I use Rootkit Hunter ([http://www.rootkit.nl/projects/rootkit_hunter.html)](http://www.rootkit.nl/projects/rootkit_hunter.html)). No compiling, very easy to install.

Hope it's of some use.

---

### Post by towsonu2003 on 2005-10-18
[QUOTE=paddyg]Perhaps not trojans, what about backdoors, rootkits or other worms?

I use Rootkit Hunter ([http://www.rootkit.nl/projects/rootkit_hunter.html)](http://www.rootkit.nl/projects/rootkit_hunter.html)). No compiling, very easy to install.

Hope it's of some use.[/QUOTE]

for the rootkits, ubuntu has chkrootkit in its repositories, officially supported. 
also, just found out that you don't have to compile this one. did not try it yet (still reading :) ).

---

### Post by ecobuntu on 2005-10-18
What do you guys use for virus protection?  ClamAV?  And what's a rootkit?

---

### Post by towsonu2003 on 2005-10-18
[QUOTE=ecobuntu]What do you guys use for virus protection?  ClamAV?  And what's a rootkit?[/QUOTE]
I don't use an antivirus program. What would be the point of using linux then?

Rootkit is (google define:) A hacker security tool that captures passwords and message traffic to and from a computer. A collection of tools that allows a hacker to provide a backdoor into a system, collect information on other systems on the network, mask the fact that the system is compromised, and much more. Rootkit is a classic example of Trojan Horse software. Rootkit is available for a wide range of operating systems. 

People say it is extemely low possibility to get one.

---

### Post by AgenT on 2005-10-18
> What would be the point of using linux then? Are you serious? You are joking, right?

As per lsof.... it is already available on Ubuntu, just type lsof!
```
man lsof
```

---

### Post by ecobuntu on 2005-10-18
So is chkrootkit something I would have to invoke?  Basically it protects me from someone trying to hack into my computer? 
Just because viruses aren't prevalent on linux doesn't mean you should use a anti-virus software.  
Do you guys use ClamAV?

---

### Post by towsonu2003 on 2005-10-18
to agent & virus & joking: not really. lack of virus was crucial for me to (try to) switch to linux (when excluding political factors).

to ecobuntu: 
1. cool nickname
2. you'll do 
sudo chkrootkit -q 
-q means quiet
make sure you know what it lists as output. it listed realplayer for me so it was fine (though I uninstalled realplayer after that hehe )
it won't protect you against rootkits but will find rootkits (I guess) on your system. 

I'll start using antivirus when linuxtoday.com gets full of new virus news (like a windows news site). 

PS. I do regular backups though

[Edit] PS2. You may want to read chkrootkit documentation as I'm a newbie too...
[Edit 2] PS3. I am not running any servers (well, hopefully...)

---

### Post by paddyg on 2005-10-19
[QUOTE=ecobuntu]
Just because viruses aren't prevalent on linux doesn't mean you should use a anti-virus software.  
Do you guys use ClamAV?[/QUOTE]

I used ClamAV with Fedora Core 1 for over a year. It was a waste of time. I think antivirus programs are quite useless. What can a virus do with such limited power as a normal user has? Well, Ubuntu (I've been using it since June) is different from Fedora as the Fedora user had no power at all, while the Ubuntu main user surprised me at first. But I think if we do backups regularly (even on the same system as another user), there shouldn't be anything to worry about.

PS: lack of virus, freedom, sense of community, political factors, that's why i moved to linux. Stability and robustness, that's why i moved away from Fedora to Ubuntu.

---

