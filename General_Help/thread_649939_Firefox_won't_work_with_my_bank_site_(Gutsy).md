---
title: "Firefox won't work with my bank site (Gutsy)"
date: 2007-12-25
forum: General Help
---

### Post by ed67 on 2007-12-25
Neither will Opera.  I'm thinking this might have something to do with ubuntu rather than firefox because firefox works fine on my windows xp machine.

It loads the site, but then after I type in my username it starts to load the next screen and stops.  Same in Opera.  Anyone have any suggestions as to what it might be?

Should have mentioned I'm allowing popups and disabled adblock plus for this.

---

### Post by dcstar on 2007-12-25
> **ed67 said:**
> Neither will Opera.  I'm thinking this might have something to do with ubuntu rather than firefox because firefox works fine on my windows xp machine.

It loads the site, but then after I type in my username it starts to load the next screen and stops.  Same in Opera.  Anyone have any suggestions as to what it might be?

Should have mentioned I'm allowing popups and disabled adblock plus for this.

Various web sites are built on the "assumption" that all of the users have Windows and specifically try to use Windows only (which means non-standard) components or features.

You should contact the bank directly and tell them of your problem, if they respond with the "We are only Windows compatible" answer then I suggest that you let them know that they are stopping an increasing percentage of their customer base from using the site.

The more people that complain about this sort of thing the more likely that this woeful (and lazy) way of building web sites will be reduced.

---

### Post by wormser on 2007-12-25
You might want to try [ies4linux]("http://www.psychocats.net/ubuntu/ies4linux").

---

### Post by iris-n on 2007-12-25
Well, when i had this problem twas a java issue, after i installed the most recent version the bank resumed working.

Which one do you have?

---

### Post by ed67 on 2007-12-25
> **iris-n said:**
> Well, when i had this problem twas a java issue, after i installed the most recent version the bank resumed working.

Which one do you have?


I'm using sun java 6 I believe.  But that makes sense, when I tried agent switcher as suggested, it gave me a script error.  How can I update?  Is there a newer version?

Thanks

---

### Post by iris-n on 2007-12-25
The newest version on the run is the 1.6.0_03.

To ascertain which one are you using, type java -version in the terminal.
If it's not this one, there might be the problem.

To change the java engine you're using you could then ```
sudo update-alternatives --config java
```  or if the Sun's isn't there you can ```
sudo apt-get install sun-java6-plugin
``` to get it.

Remember that java doesn't come installed by default with ubuntu.

---

### Post by abn91c on 2007-12-25
> **ed67 said:**
> I'm using sun java 6 I believe.  But that makes sense, when I tried agent switcher as suggested, it gave me a script error.  How can I update?  Is there a newer version?

Thanks

make sure you have the latest adobe flash player also, that may be your issue also

---

### Post by jflaker on 2007-12-25
> **ed67 said:**
> Neither will Opera.  I'm thinking this might have something to do with ubuntu rather than firefox because firefox works fine on my windows xp machine.

It loads the site, but then after I type in my username it starts to load the next screen and stops.  Same in Opera.  Anyone have any suggestions as to what it might be?

Should have mentioned I'm allowing popups and disabled adblock plus for this.

Until a solution is found, I would also suggest that until they are able to "allow" you on their website, insist that they refund you any fees associated with web access.......If the site access doesn't have fees, ask them to refund you your other fees as you are inconvenienced by their decision to not support you as a customer......again, the inconvenience factor!.

If they tell you that they don't support your browser or even OS, let them know that you can no longer be their customer.....move your account to one that does support your online banking.

(I am a little biased to the banking conglomerates.......In no other business can you get away with charging all those fees and KEEP your customer base........Banks actually charge YOU to be their customer!!)   Sorry, just a blunt opinion.

---

### Post by vishzilla on 2007-12-25
i find it very irritating when some websites adhere to Windows/IE only!!! you can try IEs4Linux as mentioned earlier

---

