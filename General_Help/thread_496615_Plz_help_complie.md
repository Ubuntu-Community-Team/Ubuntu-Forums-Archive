---
title: "Plz help complie"
date: 2007-07-09
forum: General Help
---

### Post by zanazzi on 2007-07-09
i want to try out this software [ http://linuxappfinder.com/package/kdissert ]( http://linuxappfinder.com/package/kdissert ) only i dont know how to install it, i could really do with a step by step guide, other than the one thats on teh web site (treat me like a tard :) )

many thanks

---

### Post by Vajra Vrtti on 2007-07-09
[LIST=1]
[*]Click **Add/Remove...** in the application menu.
[*]Select the **All** folder at left.
[*]Type **kdissert** in the Search field.
[*]Mark the square box at its left.
[*]Click the **Apply** button.
[/LIST]
That's it. Add/Remove is always the first place to look for desired applications.

---

### Post by zanazzi on 2007-07-09
its not in adept!!!!

and tbh i need to learn to compile :P

---

### Post by Vajra Vrtti on 2007-07-09
> its not in adept!!!!
It is (in Feisty). You have to enable the **universe** repository.
> and tbh i need to learn to compile
I don't think you will learn much. Its installation (see [here]("http://freehackers.org/~tnagy/kdissert.html")) is just a matter of running a *configuration* and an *install* scripts.

---

### Post by hooksie on 2007-07-09
Hmm, I tried doing a test configure/install, but apparently you need KDE for this program, which I don't have.  The following is untested because of that.

> 
wget [http://freehackers.org/~tnagy/kdissert/kdissert-1.0.7.tar.bz2](http://freehackers.org/~tnagy/kdissert/kdissert-1.0.7.tar.bz2)
tar -jxvf kdissert-1.0.7.tar.bz2
cd kdissert-1.0.7/
./waf configure
./waf
sudo -c “./waf install"


If you experience problems with the first and second ./waf commands, try running them under sudo, it helped me once with compiling pidgin.

I cant be sure this will work.  Confirmation from someone else would be great.

---

### Post by zanazzi on 2007-07-09
Ur advise is greatly appreciated tho im a dumb @ss !!!! lol

i found the prog while surfing and thought id try and complie it but after Vajra Vrtti's second post i thought id try 

```
 sudo atp-get install kdissert 
```

it worked ooops

sorry for wasting ur time on this thread, ill be more thoughtful and consider alternative routes to dl'ig stuff b4 asking for help 

again soz 
*bows head in shame*

---

