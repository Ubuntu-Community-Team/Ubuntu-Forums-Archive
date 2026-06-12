---
title: "Alt/Unicode characters"
date: 2007-09-08
forum: General Help
---

### Post by tonyisntcreative on 2007-09-08
I just upgraded to Feisty a couple of days ago, and so far it's been a good move.  Feisty seems to be a lot better with RAM consumption than Dapper was (and it wasn't even bad) and a few other things I couldn't seem to get working worked right away.  

But I type quite a bit.  One of the things I got very used to before was simply pressing ctrl+shift+XXXX to enter a unicode character, such as a dash.  But today when I went to do this while typing a reply on a forum, my standard ctrl+shift+2014 simply highlighted my text and made me confused.  I experimented with some different methods, like how it is done in windows (alt+xxxx), and this only made my tabs switch around.

Now before anyone mentions it, I *know* that I can pull up the character map and copy and paste and whatnot.  However, this gets very tedious and annoying; it's much easier simply to press a few buttons and not disrupt the flow I had while typing.  

If anyone knows how I should go about fixing this please help me out.  I've seen a few other threads on this forum in which others have had this same issue, but nobody seems to have fixed it.  I've found a few other instances elsewhere on the internet, but again, no help.

---

### Post by goatflyer on 2007-09-08
This may help you.

[http://ubuntuforums.org/archive/index.php/t-329987.html](http://ubuntuforums.org/archive/index.php/t-329987.html)

---

### Post by tonyisntcreative on 2007-09-09
That's the same issue I'm having, but unfortunately it doesn't look like his problem was solved, either.

I do see, however, your little bit of code posted.

When I enter the same this is my output:
```
tony@ubuntu:~$ set | grep LANG
LANG=en_US.UTF-8
```

I don't have the additional line for LANGUAGE.  I know that I've seen this en_US.UTF-8 line before, but I don't know if it will make a difference, where it should go, etc.  But if you think you might know something that I don't that's excellent; I could really use the help.

Keep in mind that this is a seems to be a problem with Feisty.  Everything worked fine with Dapper, which I'd been using for well over a year, but I also installed Feisty on our family computer and the problem affects that computer, too.

---

### Post by shirilover on 2007-09-09
Instead of Ctrl+Shift+2014, use Ctrl+Shift+u2014

---

### Post by tonyisntcreative on 2007-09-09
Wow... that was fairly simple.  Does anybody know why there has been a change?  That makes it slightly more tedious, but I suppose it's no big deal, as I can find work-arounds.

Thank you for the help!

---

