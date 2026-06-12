---
title: "Updating Firefox was a mistake..."
date: 2006-11-12
forum: General Help
---

### Post by Not-a-geek on 2006-11-12
I upgraded to FF2, on BB.  Alas, the upgrade overwrote my old FF (1.5.0.1) but did not update *all) information.  So now I cannot install new themes or extensions.  If i try to install a theme or extension that is for 2.0, I get an error message that says it is not compatible with 1.5.0.1.  If I try to install something that *is* compatible with 1.5 etc, I get an error message saying it is not compatible with 2.0.

I've been to the FF forums and the Gnome forums and browbeaten my local gurus.  The consensus seems to be that this is a result of the way Ubuntu does package installations.  So here I am at the Ubuntu fora -- *please* can someone tell me, or point me to a URL that tells me, how to get *all* of my files to know that I am using FF 2.0 so that I can use the various add-ons and themes I want?

Haval vam puno....

---

### Post by aysiu on 2006-11-12
Don't know if I can help, but it might be good to know by what method you upgraded to Firefox 2.0 in Breezy Badger.

---

### Post by Not-a-geek on 2006-11-12
> **aysiu said:**
> Don't know if I can help, but it might be good to know by what method you upgraded to Firefox 2.0 in Breezy Badger.

It is probably not helpful, since I just downloaded it and said yes to the option ot open with whatever -- I really mean it when I say I am not a geek!  It seemd to do the equivalent of aurorun in M$, and presto, changeo!  FF2.  I assune that it used whatever Ubuntu uses to do my weekly updates....

Thanks, btw....

---

### Post by aysiu on 2006-11-12
You don't have to be a geek--that's fine. Many here are not, regardless of what you might think. You do, however, have to give details in order for people to help you.

Where did you download it from? What did you download?

Please, be as specific as possible. Outline every step you took to "upgrade to Firefox 2.0."

---

### Post by Not-a-geek on 2006-11-12
I downloaded from the Firefox site, the day after FF2 came out.  When the "what shall I do with this file"  box came up, I chose the open with whatever  (usually it is archive manager).  After that, things ran pretty automatically, and I don't really remember anything else.  I fear I was not as diligent as I should have been....

I have to go and feed and medicate 13 sick cats right now, but i will be checking back as I nurse my scratches....

---

### Post by Not-a-geek on 2006-11-12
Oh, and the what was the linux version of FF2, through the standard button.  No bells, no whistles, no other applications.....

---

### Post by aysiu on 2006-11-12
The archive manager part sounds about right, but I can't remember there being an installer version of Firefox for Linux. As far as I know, it's a zipped up .tar.gz file with a bunch of files and an executable--nothing should be running "pretty automatically."

Well, I know at least one part of the equation. Firefox 2.0 from Mozilla's website does not integrate with Ubuntu--it's its own thing. I'm not sure what directory you installed it to, but it's very likely you have two co-existent Firefoxes and you're launching one one time and the other another time.

Your best bet, if you want to install Firefox 2.0 to integrate well with Ubuntu is to use this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

It requires only two terminal commands, which you can copy and paste into the terminal. You don't have to type one damn thing.

The script fetches the latest Firefox from Mozilla, asks what locale version you want, and then integrates Firefox with your launchers and plugins. If you need any help with using the script, please let me know.

---

### Post by Not-a-geek on 2006-11-12
Havla vam puno!  I shall try it out tomorrow, as I think I should be awake for this one!

And many thanks again!  Sure hope it works.

ttys

someday-a-geek!~

---

### Post by aysiu on 2006-11-12
> **Not-a-geek said:**
> Havla vam puno!  I shall try it out tomorrow, as I think I should be awake for this one!

And many thanks again!  Sure hope it works.

ttys

someday-a-geek!~
Please post back the results.

---

