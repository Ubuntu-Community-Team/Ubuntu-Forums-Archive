---
title: "keyboard hastle"
date: 2008-06-28
forum: General Help
---

### Post by ratdog on 2008-06-28
Hello, I just did a new install of Hardy Heron and my keyboard settings are a little messed up.   My problem is with the apostrophe and quotes key.  Instead of typing an apostrophe, it types nothing and then puts an accent over the next letter I type.  Pretty much the same with the quotes.  Instead of typing a quotation symbol it puts 2 dots over the next letter I type like this ë.

Please, how do I fix this.  My girlfriend is a stickler for grammar and gives me a hard time when I write her emails without proper punctuation.:)

---

### Post by Elfy on 2008-06-28
I would say it's set up with the wrong location, system > preferences > keyboard should allow you to set it up

---

### Post by ratdog on 2008-06-28
Yeah, Ive tried all the US and Canada layouts that look close, but all of them mess up that one key for some reason.  I was hoping there was a way to customize a layout or something.

---

### Post by Elfy on 2008-06-28
It appears I can't even play about with my keyboard layouts to try - I've got my own thread now as well :)

I assume you have tried to see if you're keyboard is actually represented in the keyboard models on the layouts page then.

There do appear to be a lot of threads regarding similar problems, but as I can't either look at the layouts in my keyboard layout application nor have a 'foreign' keyboard I'm not sure if any of the thread are applicable to you.

These are the searches I was using 

[http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=keyboard+layout++apostrophe+key&sa.x=48&sa.y=19](http://www.uboontu.com/results.htm?cx=002072379199720138921%3A9m-bgfzutzq&cof=FORID%3A10&q=keyboard+layout++apostrophe+key&sa.x=48&sa.y=19)

Perhaps have a look through as you know what you'r ekbd looks like.

It does appear that you can customise keys to suit though.

---

### Post by drs305 on 2008-06-28
xmodmap can change key designations. I would consider this a temporary fix until you can find a keyboard setting that works.

Run the following command to find the keycode value of the desired key:
```
xev
```

With the small box in foreground, press the problem key and note the keycode value. I would expect it to be 48, but check since your keyboard may be different.
Then run this:
```
 xmodmap -e 'keycode **keycodenumber** = apostrophe quotedbl'
```
Example: xmodmap -e 'keycode 48 = apostrophe quotedbl'

That should ensure the correct signal is sent and *may* correct the problem. To make it permanent, put this command in the System, Preferences, Sessions, Startup Programs folder, Add.

---

