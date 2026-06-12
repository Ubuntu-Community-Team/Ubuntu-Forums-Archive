---
title: "I thought Ubuntu would be more stable/faster than XP but..."
date: 2008-01-08
forum: General Help
---

### Post by al2six on 2008-01-08
So i wanted to copy some HTML off a website. I view source in firefox, find the selected code I want to copy, start highlighting and the browser freezes. I restart firefox, same thing happens. I restart the computer, open firefox, same thing happens. I save the html file to my hard drive (280 kb), open it up in gedit, try to highlight some text and it freezes. I restart and try a few more times to no avail.

Then i restart the computer, boot into XP, open the file off my hard drive, select the text, copy it, do find and replace, etc, etc all without the slightest hesitation from XP.

what gives? every person who told me i just HAD to try linux would tell me that these kinds of problems happen all the time with windows but never with linux, but my experience was quite the opposite.

---

### Post by Sef on 2008-01-08
> Then i restart the computer, boot into XP, open the file off my hard drive, select the text, copy it, do find and replace, etc, etc all without the slightest hesitation from XP.

What browser did you use?

---

### Post by jespdj on 2008-01-08
> **al2six said:**
> what gives? every person who told me i just HAD to try linux would tell me that these kinds of problems happen all the time with windows but never with linux, but my experience was quite the opposite.
So you had a little problem with a certain browser on Linux and then you blame the whole OS for being not stable and not fast? :confused:

---

### Post by eye208 on 2008-01-08
> **al2six said:**
> I view source in firefox, find the selected code I want to copy, start highlighting and the browser freezes. I restart firefox, same thing happens. I restart the computer, open firefox, same thing happens. I save the html file to my hard drive (280 kb), open it up in gedit, try to highlight some text and it freezes.
Does this mean the application (Firefox, GEdit) freezes or the entire desktop?

---

### Post by sonofusion82 on 2008-01-08
haha.. probably bcoz you are trying to steal other ppls code and you get punished for that :-p

---

### Post by al2six on 2008-01-08
> **sonofusion82 said:**
> haha.. probably bcoz you are trying to steal other ppls code and you get punished for that :-pactually i was copying a table of data from a  press release, smartass, but thanks for your valuable input.

---

### Post by al2six on 2008-01-08
> **eye208 said:**
> Does this mean the application (Firefox, GEdit) freezes or the entire desktop?

the application froze (both firefox and gedit)

---

### Post by al2six on 2008-01-08
> **jespdj said:**
> So you had a little problem with a certain browser on Linux and then you blame the whole OS for being not stable and not fast? :confused:
firefox and gedit both couldn't handle a 280 kb file. if it's not the OS, i'm all ears; tell me what it is and how to fix it

---

### Post by eye208 on 2008-01-08
> **al2six said:**
> the application froze (both firefox and gedit)
Do they freeze every time you select some text with the mouse? Or does it happen only with that particular HTML code? Can you post the code or the website URL here so we can check this?

---

### Post by al2six on 2008-01-08
well there was only one area of code I was trying to copy, so I don't know if it happens everywhere or just at that one spot. Here's the url: [http://media.gm.com/servlet/GatewayServlet?target=http://image.emerald.gm.com/gmnews/viewmonthlyreleasedetail.do?domain=74&docid=42261](http://media.gm.com/servlet/GatewayServlet?target=http://image.emerald.gm.com/gmnews/viewmonthlyreleasedetail.do?domain=74&docid=42261)

I was trying to copy the table with all the sales figures

---

### Post by bobyy on 2008-01-08
Hy man ..
I tryed..and for me it is ok .no problem ...sorry for your problem 
don`t blame whole OS for that 
for me Firefox freezing whem i play some particular web pages (xxx) .. :))
but is a VLC pluggin bug...

peace...

---

### Post by Maikelv on 2008-01-08
maybe a stupid question, but have you tried rebooting ?

---

### Post by gunbladeiv on 2008-01-08
i've tried to view source like you did.. and my firefox works and do not hang in the middle of the process.  Maybe you need to tell us specifically of what went wrong there?

i dont think Ubuntu cause the problem as the kernel not panic at all.  May be it's just some problem with firefox itself.  Or maybe with what you are doing. MAYBE..

---

### Post by eye208 on 2008-01-08
> **al2six said:**
> I was trying to copy the table with all the sales figures
I think I can see your problem now. Marking the table and copying it over to GEdit works fine, but when I switch GEdit to HTML syntax highlight mode, it freezes. I guess this is because the table is 202,438 bytes in a single line. GEdit seems unable to handle lines that long in syntax highlight mode.

You can use ["tidy"](http://packages.ubuntu.com/gutsy/web/tidy) to clean up and format the code before loading it into GEdit. Or try a proper HTML editor such as [Bluefish](http://packages.ubuntu.com/gutsy/web/bluefish). GEdit is really just the Notepad.exe of Gnome.

---

### Post by OpenFish on 2008-01-08
i agree it is probably a firefox prob i tryed and my ice weasel didnt have prob copying it to gedit so i is suprised firefox had a prob

may i suggest running firefox from a terminal and see if there is any output there thats what i always do first when i get a freeze or a fail at run time i've fixed loads of problems from the terminal read out pitticaly multi media programs (irony?)

in fact i by fare prefer tui's over gui's for all math programs and a lot of others

---

### Post by eye208 on 2008-01-09
> **OpenFish said:**
> i agree it is probably a firefox prob i tryed and my ice weasel didnt have prob copying it to gedit so i is suprised firefox had a prob
Did you read my post?

---

