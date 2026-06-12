---
title: "[SOLVED] Strnage Grep Behaviour"
date: 2008-05-26
forum: General Help
---

### Post by slibuntu on 2008-05-26
Dunno if this is serious newbie stuff that I havent heard before, but when I typed grep .* into the terminal, i got o/p that looked like this - 

[IMG]http://compsoc.nuigalway.ie/~slibuntu/Screenshot.png[/IMG]
Is this a bug??

---

### Post by VMC on 2008-05-26
> **slibuntu said:**
> Dunno if this is serious newbie stuff that I havent heard before, but when I typed grep .* into the terminal, i got o/p that looked like this - 

[IMG]http://compsoc.nuigalway.ie/~slibuntu/Screenshot.png[/IMG]
Is this a bug??

Are you sure you type grub and not cat? If you type grub by itself what happens, or something simple like $ echo junk|grep junk , do you get junk as o/p?
When I type grep .* I get what's expected.

---

### Post by Gunman1982 on 2008-05-26
I guess the problem is that grep outputs all hidden files (including binary ones) and that ***** up your console. Press ctrl+C to abort the grep (if its still running ;) ) and type 'reset' to reset the console.

---

### Post by ibuclaw on 2008-05-26
Type in:
```

env reset && clear
```
To reset everything back to normal.

Though a strong word of advice.

**NEVER USE .* IN AN EXPRESSION MATCHING COMMAND**

Always include a letter to go with it. (ie: "**.a***")

The only reason I can think of this strange thing happening, is because:

QUOTE **man find**:
> 
Each directory on a normal Unix filesystem has at least 2 hard  links:  its  name  and  its  **&#8216;.&#8217;** entry.   Additionally,  its  subdirectories (if any) each have a **&#8216;..&#8217;**  entry linked to that directory.


I am thinking that grep is including these hardlinks when it searches through the files.

But, anyhow. As I said before.
Don't ever run any expression matching tool with just ".*" as the expression in it.

Regards
Iain

---

### Post by slibuntu on 2008-05-26
The funny thing is, it has stopped! The last line of the output there is the prompt waiting for input, and if you type, all characters come out in whatever font/language that is!

Closing the terminal sets everything back to normal, it seems to change the laguage or font to something weird.

Screen capture vid - [http://compsoc.nuigalway.ie/~slibuntu/out.ogg](http://compsoc.nuigalway.ie/~slibuntu/out.ogg)

tinivole is more than likely right, it includes all the . and .. files aswell. So it's possibly not a good idea to run it.

---

### Post by ibuclaw on 2008-05-26
> **slibuntu said:**
> The funny thing is, it has stopped! The last line of the output there is the prompt waiting for input, and if you type, all characters come out in whatever font/language that is!

Closing the terminal sets everything back to normal, it seems to change the laguage or font to something weird.

Screen capture vid - [http://compsoc.nuigalway.ie/~slibuntu/out.ogg](http://compsoc.nuigalway.ie/~slibuntu/out.ogg)

tinivole is more than likely right, it includes all the . and .. files aswell. So it's possibly not a good idea to run it.

(Just seen the video)
Yes, it may seem like gibberish letters, but it the terminal can still operate in the same way.

As I said in my previous post, typing in "**env reset && clear**" resets it all, even though you can't see the letters that you type in.

And nice desktop too! :D

I see you have Future Looks.
I have that too. Except that I dyed everything orange to match the Ubuntu Look. :)

Also removed any distractions (such as cube) for more pleasing tools (2x2 desktop wall).

Regards
Iain

---

### Post by slibuntu on 2008-05-27
Damn sexy!! lovin futurelooks it must be said, looks so smooth and sleek!

---

### Post by slibuntu on 2009-01-07
Figured out a bit of backup info to this.

It seems the terminal may be switching to binary. 

See this page, the first tip is in relation to it.
[http://www.linuxformat.co.uk/wiki/index.php/58_Cool_Hacks]("http://www.linuxformat.co.uk/wiki/index.php/58_Cool_Hacks")

---

