---
title: "Thunderbird"
date: 2007-01-21
forum: General Help
---

### Post by CheeseQueen452 on 2007-01-21
Is anyone using the webmail/yahoo extensions with Thunderbird? I've been using it with my ISP's smtp server, but there seems to be major delays with sending messages(the recipient doesn't get the email right away). I've tried sending with other servers & ports but only my ISP's smtp server works. If anyone can help, I'd appreciate it!

---

### Post by teaker1s on 2007-01-21
googlemail is free,  I have an account and it sends and receives faultlessly with thunderbird

---

### Post by CheeseQueen452 on 2007-01-21
I don't want a gmail account. I need help with Yahoo.

> **teaker1s said:**
> googlemail is free,  I have an account and it sends and receives faultlessly with thunderbird

---

### Post by Amackera on 2007-01-21
I'm not sure that that is an issue with Thunderbird. I think that it is more likely due to Yahoo!'s internal functionality. Don't quote me on that though.

---

### Post by teaker1s on 2007-01-21
looks like you need to pay to use thunderbird with yahoo-see link
[http://help.yahoo.com/mail/pop/pop-06.html]("http://help.yahoo.com/mail/pop/pop-06.html")

---

### Post by CheeseQueen452 on 2007-01-22
I'm not saying it's an issue with TB, I think it's my ISP's smtp server that's causing the delays. That's why I want to try a different server, but it seems that only my ISP's server works.

> **Amackera said:**
> I'm not sure that that is an issue with Thunderbird. I think that it is more likely due to Yahoo!'s internal functionality. Don't quote me on that though.

---

### Post by phossal on 2007-01-22
It doesn't matter what you use with Yahoo. There are always significant delays. Things are quite messy on their back end. ;) It's not Thunderbird.

---

### Post by CheeseQueen452 on 2007-01-22
I'm guessing you're not familiar with the webmail extension.... The extension is to download email from services that don't offer free pop access, such as Yahoo. It may sound illegal, but it's not.

> **teaker1s said:**
> looks like you need to pay to use thunderbird with yahoo-see link
[http://help.yahoo.com/mail/pop/pop-06.html]("http://help.yahoo.com/mail/pop/pop-06.html")

---

### Post by CheeseQueen452 on 2007-01-22
As I said before, I don't think it's TB but rather the smtp server I'm using. To give you an example, when I send a message to Yahoo Groups, there have been delays of as much as 2 days before the message appears at the group website & my inbox. And I'm not even moderated.... the messages should appear within a few minutes, but much of the time there's a delay as I described above. Other Yahoo Group members' posts seem to come through quickly, as they normally should.

> **phossal said:**
> It doesn't matter what you use with Yahoo. There are always significant delays. Things are quite messy on their back end. ;) It's not Thunderbird.

---

### Post by AmandaKerik on 2007-02-01
I'm using the webmail add-on for Thunderbird, and incoming it works great! I haven't tried outgoing yet. Shall I let you know what it's like when I try it?

---

### Post by CheeseQueen452 on 2007-02-01
I assume you're using the Yahoo extension, correct? Sending mail supposedly works using "localhost" as the server. If it works for you, let me know what settings you're using.

> **AmandaKerik said:**
> I'm using the webmail add-on for Thunderbird, and incoming it works great! I haven't tried outgoing yet. Shall I let you know what it's like when I try it?

---

### Post by AmandaKerik on 2007-02-01
Sure!

After I got the webmail and yahoo add-ons installed, I went into Webmail's settings:
Tools > Extensions > Webmail > [Preferences] > [Servers] > Ports
And set the pop3 port to 1111 and the smtp port to 1112. 

I have a few bad habits from XP, so I clicked [ok] to everything and restarted Thunderbird again (I don't think you have to).
Check that the Webmail is saying everything's working by going into:
Tools > Extensions > Webmail > [Preferences] > [Servers] > Status
The first two "lights" should be green.

Now go into your yahoo accounts settings, and change the ports to match.

I find that having all "IDs" and "Names" in the wizard set to your full yahoo email address will help too.

---

### Post by CheeseQueen452 on 2007-02-01
Well, this didn't work for me. What server did you use to send with? Did you use SSL? Is your Yahoo account beta or classic? I tried using localhost on port 1112, but it didn't work.

> **AmandaKerik said:**
> Sure!

After I got the webmail and yahoo add-ons installed, I went into Webmail's settings:
Tools > Extensions > Webmail > [Preferences] > [Servers] > Ports
And set the pop3 port to 1111 and the smtp port to 1112. 

I have a few bad habits from XP, so I clicked [ok] to everything and restarted Thunderbird again (I don't think you have to).
Check that the Webmail is saying everything's working by going into:
Tools > Extensions > Webmail > [Preferences] > [Servers] > Status
The first two "lights" should be green.

Now go into your yahoo accounts settings, and change the ports to match.

I find that having all "IDs" and "Names" in the wizard set to your full yahoo email address will help too.

---

### Post by AmandaKerik on 2007-02-02
Sending and recieving servers are both "localhost".
I'd set it up with no encryption / ssl and make sure it works, then start tinkering with the security settings.
I use classic, but I believe that Webmail will work with beta as well...
I have classic because when I check my mail manually in Firefox, I can then block ALL the ads with a couple add-ons and tinkering (Adblock Plus and Stylish). Even the text ads above and below the menu are gone for me :D

"Now go into your yahoo accounts settings, and change the ports to match."
I meant this to mean your yahoo account settings in Thunderbird.

And I plan on having a walkthrough on a site I'm setting up shortly, complete with screenshots... I'll stick the link in my signature on here when it's done.

---

### Post by CheeseQueen452 on 2007-02-03
I was able to send with my account in classic mode, but when I posted to Yahoo groups, my messages didn't appear as they should. For instance, spaces between some words were missing even though I put in the spaces, & there was only 1 or 2 words on every other line.

Try it in beta mode, & let me know if you have any success sending. I've only been able to send using my ISP's smtp server. Nothing else I've tried works, so I'm hoping there's something that I've simply overlooked. What I'm trying to accomplish with all of this, is to hopefully avoid the delays I've been seeing with my messages to Yahoo groups. Sometimes, my posts don't come back to me for 2 days!

> **AmandaKerik said:**
> Sending and recieving servers are both "localhost".
I'd set it up with no encryption / ssl and make sure it works, then start tinkering with the security settings.
I use classic, but I believe that Webmail will work with beta as well...

---

### Post by AmandaKerik on 2007-02-03
If you try to connect to yahoo beta, it comes back with a funny error message:
Sending of password did not succeed. Mail server local host responded: Negative vibes from <youre-mailaddress>

:lolflag:

---

### Post by CheeseQueen452 on 2007-02-03
Did you set BOTH your account & the extension to beta? Let me know what happens....

> **AmandaKerik said:**
> If you try to connect to yahoo beta, it comes back with a funny error message:
Sending of password did not succeed. Mail server local host responded: Negative vibes from <youre-mailaddress>

:lolflag:

---

### Post by AmandaKerik on 2007-02-04
Nope, I didn't go into both add-ons and look for the Beta options... I figured it wasn't covered by them yet (it's touch and go in ypops).

I'll try it in a bit...

---

### Post by Cochese on 2007-02-05
I can't get any port to give me a green light on POP or SMTP in Webmail.

I've tried 1024, 1110, 2110, 9110, 1030, 1040 for POP and others similar to 1025, 1125 , 9025 for SMTP.

Nothing works. Is there a setting somewhere I am missing?

---

### Post by CheeseQueen452 on 2007-02-05
For POP I use port 1200. For SMTP, I use port 25 with my ISP's smtp server, which is what I would like to change but nothing else I've tried works for me. If you have any success, let me know.

> **Cochese said:**
> I can't get any port to give me a green light on POP or SMTP in Webmail.

I've tried 1024, 1110, 2110, 9110, 1030, 1040 for POP and others similar to 1025, 1125 , 9025 for SMTP.

Nothing works. Is there a setting somewhere I am missing?

---

### Post by Cochese on 2007-02-05
1200 didn't work for me.
Hmmm, not sure what to do

I'll keep trying different ports

---

### Post by AmandaKerik on 2007-02-05
> **Cochese said:**
> I can't get any port to give me a green light on POP or SMTP in Webmail.
I've tried 1024, 1110, 2110, 9110, 1030, 1040 for POP and others similar to 1025, 1125 , 9025 for SMTP.
Nothing works. Is there a setting somewhere I am missing?

I know it's frustrating - it should work but doesn't, and you can't quite figure out why. :( 
What steps are you taking, exactly? Give me a quick run-through (while you try it, yet again)... I might be able to spot a step you skip.

---

### Post by CheeseQueen452 on 2007-02-06
When you change ports, make sure you change it in BOTH the extension & TB account settings. Then restart TB & try sending/receiving.

> **Cochese said:**
> 1200 didn't work for me.
Hmmm, not sure what to do

I'll keep trying different ports

---

### Post by Cochese on 2007-02-06
Okay, first I download the extensions into my tbird extension folder.  Then, start tbird and install the extensions.  Then, check the main webmail ext. and set the ports(or leave them deafult), check server settings on both accounts and make sure they match ports POP and SMTP and that both are set to localhost. Restart tbird and check for green light.

I have been messing with firestarter to see if I can open various ports and make it work because it wasn't working before I installed it. It seems weird that webmail can't get through but my gmail accounts can get through 995 without webmail just fine. I tried 995 for webmail and that didn't work either.

What am I missing:confused:

---

### Post by CheeseQueen452 on 2007-02-06
Localhost doesn't work for smtp under the Yahoo Mail beta setting, although I've been told it does work but I think that's for window$.

> **Cochese said:**
> Okay, first I download the extensions into my tbird extension folder.  Then, start tbird and install the extensions.  Then, check the main webmail ext. and set the ports(or leave them deafult), check server settings on both accounts and make sure they match ports POP and SMTP and that both are set to localhost. Restart tbird and check for green light.

---

### Post by AmandaKerik on 2007-02-06
> **Cochese said:**
> ...Then, start tbird and install the extensions.  Then, check the main webmail ext. and set the ports...

You need to restart TB right after you install the add-ons into it - so it can recognise what it is, etc. I don't think it'll mess up things that much, though.

I would suggest you switch your yahoo mail back over to classic - it may work better.

Remember - if you change the ports, you NEED to restart TB.

There's an update to webmail:yahoo as well... I just got it today.

---

### Post by Cochese on 2007-02-07
I think I figured out the problem, but I am not sure. It's working now, will someone tell me if this was the problem?

In firestarter I would watch the current activities and blocked access windows to see if the firewall was blocking anything while I was running tbird.  Well, tibird was going through just fine on port 995 and nothing was being blocked, and i saw nothing of localhost or 127.0.0.1 being blocked or making an attempt to connect anywhere.

So I checked my /etc/network/interfaces file and noticed that "auto lo" was missing under "iface lo inet loopback".
I must have accidently removed it when I was configuring my wireless card.:oops:   So I fixed it, rebooted, and went back to tbird and now it is working.

So it was disabled correct? That's why I couldn't get localhost to do anything?

---

### Post by CheeseQueen452 on 2007-02-07
Hmm, sounds like that was the problem. Well, let me know if you have any success sending with your Yahoo account(& the extension) set to beta.

> **Cochese said:**
> I think I figured out the problem, but I am not sure. It's working now, will someone tell me if this was the problem?

In firestarter I would watch the current activities and blocked access windows to see if the firewall was blocking anything while I was running tbird.  Well, tibird was going through just fine on port 995 and nothing was being blocked, and i saw nothing of localhost or 127.0.0.1 being blocked or making an attempt to connect anywhere.

So I checked my /etc/network/interfaces file and noticed that "auto lo" was missing under "iface lo inet loopback".
I must have accidently removed it when I was configuring my wireless card.:oops:   So I fixed it, rebooted, and went back to tbird and now it is working.

So it was disabled correct? That's why I couldn't get localhost to do anything?

---

### Post by Cubsnut2 on 2007-02-14
I've got a funny situation.  I got Thunderbird to work with a hotmail account and a yahoo account, but i can't get it to work with a second yahoo account.  I keep getting the bad vibe message on the password submission.  Can it support 2 yahoo mail accounts??

thanks,
CN2

---

### Post by CheeseQueen452 on 2007-02-14
Is your 2nd Yahoo account set to beta or classic? If the extension is set to beta, the account must also be beta.

> **Cubsnut2 said:**
> I've got a funny situation.  I got Thunderbird to work with a hotmail account and a yahoo account, but i can't get it to work with a second yahoo account.  I keep getting the bad vibe message on the password submission.  Can it support 2 yahoo mail accounts??

thanks,
CN2

---

