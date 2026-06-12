---
title: "how to install scripts in the gimp?"
date: 2006-12-20
forum: General Help
---

### Post by syxbit on 2006-12-20
first, I think it's disgraceful that the gimp doesn't have a redeye removal tool out of the box.
I looked around on how to do this, and found a few walkthrough's on doing it.
who on earth wants to spend 10 mins doing this with the fuzzy select tool, and then filtering colours?
I think i'm going to go back to dual boot so i can run photoshop.
still, i ended up installing picasa which does it just fine.
now, on to the question ;)
I read 2 different ways to install scripts (i'm trying to install redeye.c)
1st said to type this into the terminal
```
gimp-tool-2.0 --install redeye.c
```
others said slightly differently
none worked.
I also read about a forum member having to install "gimp-tool", but i couldn't find it in synaptic.
why should something as basic as redeye cause me so many problems?
i didn't think i was a linux n00b, but maybe i am :(

---

### Post by jrib on 2006-12-20
Here's the official documentaiton from GIMP on installing plugins: [http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install](http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install) .

The gimptool-2.0 command is included in the libgimp2.0-dev package.  So you should be able to just install the libgimp2.0-dev package ```
sudo aptitude install libgimp2.0-dev
``` and then run the command you need (you seem to have a typo in yours): ```
gimptool-2.0 --install redeye.c 
```.  If it fails, be sure to paste the command as well as the output.

---

### Post by syxbit on 2006-12-21
> **_jason said:**
> Here's the official documentaiton from GIMP on installing plugins: [http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install](http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install) .

The gimptool-2.0 command is included in the libgimp2.0-dev package.  So you should be able to just install the libgimp2.0-dev package ```
sudo aptitude install libgimp2.0-dev
``` and then run the command you need (you seem to have a typo in yours): ```
gimptool-2.0 --install redeye.c 
```.  If it fails, be sure to paste the command as well as the output.

thanks for the help
it worked
unfortunately the script is awful.
on auto mode, it turns my lips blue!
I think I'll just use Picasa for redeye reduction.....

---

