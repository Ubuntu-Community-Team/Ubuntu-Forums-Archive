---
title: "Hacker?"
date: 2005-06-01
forum: General Help
---

### Post by Das Ein on 2005-06-01
What does this mean?

[[IMG]http://img224.echo.cx/img224/7040/wtf8ro.th.png[/IMG]](http://img224.echo.cx/my.php?image=wtf8ro.png)

---

### Post by netrattler on 2005-06-01
It means that someone was trying to gain access to remotely control your desktop if you dont use this feature you can disable it by going to System -> Preferences -> Remote Desktop -> and uncheck Allow other users to view your desktop. Rule of thumb never allow access unless you know who it is. You might also want to run this command from a terminal if you decide to leave this feature on to see if anyone has gained access to one of your user accounts run "who" and it will tell you what users are logged on to your system or check your log files.

Joe

---

### Post by Das Ein on 2005-06-01
"It means that someone was trying to gain access to remotely control your desktop"
What would this do? What happens if I don't uncheck it, and I allow the person to do it?

---

### Post by netrattler on 2005-06-01
Basically it would allow him to control your mouse cursor and view your display to do what he wants.

Joe

---

### Post by Das Ein on 2005-06-01
[QUOTE=netrattler]Basically it would allow him to control your mouse cursor and view your display to do what he wants.

Joe[/QUOTE]
Not good. If I accedently allow it can I stop him?
What happens if I let thoose error messages go, and don't say decline or allow?

---

### Post by netrattler on 2005-06-01
Yeah you can always close the session and stop him if your at the computer and see it going on. Just hit the decline button. But if you don't use this feature I would disable it, then you don't have to worry about it. You can always start it up again if you decide  you need it later.

Joe

---

### Post by Das Ein on 2005-06-01
I was gone today, so odviosuly they wern't accepted or declined, would that do anything.

---

### Post by bored2k on 2005-06-01
[QUOTE=Das Ein]I was gone today, so odviosuly they wern't accepted or declined, would that do anything.[/QUOTE]
 The question is: How did that Remote Session got enabled. This is disabled by default.

---

### Post by netrattler on 2005-06-01
Another thing I would check right now is your system log and make sure none of your user accounts have been compromised. Just go to Applications -> System Tools -> System Log. Look down the list to see if any users were not suppose to be logged on at that time. What your looking for is something that looks a little like this "session opened for username"

Joe

---

### Post by vega44 on 2005-06-01
[QUOTE=][/QUOTE]
 yes, some one is trying to get in your computer, so yes i would call that a threat.......

---

### Post by Das Ein on 2005-06-01
[QUOTE=bored2k]The question is: How did that Remote Session got enabled. This is disabled by default.[/QUOTE]
I never messed with it.

All users are root.

---

### Post by netrattler on 2005-06-01
Did you enable the root account on your computer following the ubuntuguide, if you didn't then I would change all your passwords on your user accounts.Disable the root account if you did or he did because you should be using sudo for administration. Then you will have to edit your user accounts to correct access permissions.

Joe

---

### Post by Das Ein on 2005-06-01
[QUOTE=netrattler]Did you enable the root account on your computer following the ubuntuguide, if you didn't then I would change all your passwords on your user accounts.Disable the root account if you did or he did because you should be using sudo for administration. Then you will have to edit your user accounts to correct access permissions.

Joe[/QUOTE]
Ubuntu guide? I am the only one using this computer, and I am the only account.
I thin I am sudo, because when I type in the command promt it says sudo for everything.

---

### Post by netrattler on 2005-06-02
Also not sure if your running ssh server or not if you are you might want to stop that service for now until you can find out what type of compromise and damage was done.

Joe

---

### Post by Das Ein on 2005-06-02
[QUOTE=netrattler]Also not sure if your running ssh server or not if you are you might want to stop that service for now until you can find out what type of compromise and damage was done.

Joe[/QUOTE]
I r teh n00b. I have no clue what you are talking about.
I know next to nothing about linux. I also can't see why anyone would want to attack me.
Any ideas?

---

### Post by netrattler on 2005-06-02
Well if your the only account on that computer and you didn't enable the root account changing your password on your account should suffice.

Joe

---

### Post by netrattler on 2005-06-02
Probably someone running a port scanner tyring to find open ports on peoples computers and just happened to stumble across you.

Joe

---

### Post by Das Ein on 2005-06-02
[QUOTE=netrattler]Probably someone running a port scanner tyring to find open ports on peoples computers and just happened to stumble across you.

Joe[/QUOTE]
What could my computer be of use to anyone? Server space?
Can I do the same thing?

---

### Post by netrattler on 2005-06-02
Not sure if you setup a firewall or not, you might want to check into that if your not running one. But if your not familiar with how one works you will have to read up on it.

Joe

---

### Post by netrattler on 2005-06-02
Once someone has gained access they can pretty much do what they want, a big thing now days is identity theft and stealing credit card information.

Joe

---

### Post by Das Ein on 2005-06-02
[QUOTE=netrattler]Once someone has gained access they can pretty much do what they want, a big thing now days is identity theft and stealing credit card information.

Joe[/QUOTE]
But I haven't bought anything online. As a matter of fact all I do is surf the web.
Is there a way I can view his computer?

---

### Post by netrattler on 2005-06-02
I was just saying it was a possibility that was the type of information that he was looking for every cracker has different reasons.

Joe

---

### Post by KLineD on 2005-06-02
[QUOTE=Das Ein]But I haven't bought anything online. As a matter of fact all I do is surf the web.
Is there a way I can view his computer?[/QUOTE]

No. Unless you happen to know the attackers IP and that he/she has the remote desktop feature enabled and he allows you to control the desktop.

---

### Post by Das Ein on 2005-06-02
[QUOTE=KLineD]No. Unless you happen to know the attackers IP and that he/she has the remote desktop feature enabled and he allows you to control the desktop.[/QUOTE]
I odviously know there IP since when they attacked me it was displayed. Just curious how would I do this?

---

### Post by benplaut on 2005-06-02
[QUOTE=KLineD]No. Unless you happen to know the attackers IP and that he/she has the remote desktop feature enabled and he allows you to control the desktop.[/QUOTE]

and... most people wouldn't have remote desktop on... basic security  :wink:

(and publishing your IP online is stupid... BTW, my IP is 192.168.0.4  :grin: )

---

### Post by KLineD on 2005-06-02
[QUOTE=Das Ein]I odviously know there IP since when they attacked me it was displayed. Just curious how would I do this?[/QUOTE]

Well, most ppl (here anyway) have dynamic IP, this means it changes and it's not always the same.

And if you look carefully in the remote desktop preferences, there you can find a line thay says exactly how users can view your desktop

---

### Post by Das Ein on 2005-06-02
[QUOTE=KLineD]
And if you look carefully in the remote desktop preferences, there you can find a line thay says exactly how users can view your desktop[/QUOTE]
I know, but how can I view other. Rember I r teh n00b.

---

### Post by KLineD on 2005-06-02
As I said, you'll have to know the ip of the person you want to connect to.

That feature is mostly intented for legit use, that means something like your mom wants her computer fixed but you dont want to be going to your parents house everytime it gets broken, so you set up a vnc server in their PC and then you can control their PC remotely.

It's also used as remote administration and things like that. Don't think you can open some application and see a bunch of ppl to which you can connect and see/control their desktop (actually, you can do something like that if you do a portscan to some ip range as described above but that's a bad thing to do).

---

### Post by Das Ein on 2005-06-02
I have no intenstion of using it, I am just curious.
Can you give me the command to view someone's ip with simplier terms?
Does it work cross OS?

---

### Post by KLineD on 2005-06-02
sorry as far as I know there's no way you can view someones ip with a command like viewip thatguy or something like that.

For example to view my IP you'll have to establish a direct connection with me (like sending a file) and then you could. Actually there are many other ways but that's out of discussion.

If you want to view your ip you could use ifconfig.

Hope it gets clearer...

And yes, your IP is plataform independent. If you have broadband and your ISP assigns your ip automatically, you get the same if you are using windows or linux or any other os.

---

### Post by Das Ein on 2005-06-02
I am sorry I said "Can you give me the command to view someone's ip with simplier terms?"
I meant "Can you give me the command to view someone's screen with simplier terms?"

---

### Post by KLineD on 2005-06-02
in the terminal:
vncviewer IP

where ip is the ip of the person which desktop you want to see and has a vnc server running.

---

### Post by Seti on 2005-06-02
If you get that message again you can use whois to try and determine who they are from their IP
in a console just```
whois xxx.xxx.xxx.xxx
``` 

or if you like the more complicated GUI version, go to Applications>System Tools>Network Tools.

This would at least tell you who her/his ISP is so you could lodge a complaint. Sometimes this works!

---

### Post by Das Ein on 2005-06-02
[QUOTE=Seti]If you get that message again you can use whois to try and determine who they are from their IP
in a console just```
whois xxx.xxx.xxx.xxx
``` 

or if you like the more complicated GUI version, go to Applications>System Tools>Network Tools.

This would at least tell you who her/his ISP is so you could lodge a complaint. Sometimes this works![/QUOTE]
Weird it was a buisness in italy. Some employee must be really bored.

---

