---
title: "Custom Russian keyboard table file for SCIM?"
date: 2007-11-07
forum: General Help
---

### Post by tbg58 on 2007-11-07
Greetings to the forum.

I've been using Ubuntu since Breezy, and I think this probably is fairly simple to do, but I can't get my fingers around how to do so.
I do translation work in Russian - volunteer stuff mostly - and correspond with Russian friends in Moscow where I lived.  But I'm an American and touch type in English.  The Yawerty layout provided with SCIM is fairly nice, but I have been using a slightly different phonetic equivalent layout (AATSEEL) for a number of years.  I found the Yawerty key map and was able to successfully edit the text 
I had figured out how to modify older .kmap files to do the trick, but SCIM appears to use a binary table file. 

I think the binary table file is the one used by SCIM, and even though I have edited the text portion of the file properly obviously the actual keys are in the binary bit.

Does anyone know of a tutorial on creating custom SCIM table files?

I read the article by Janusz Prusaczyk on the SCIM web site entitled, "How to create a new IME in about 15 minutes with SCIM and scim-tables", and I think this is exactly what I need, but I'm still having trouble understanding it.  Still a n00b in many areas, I must confess.

Any help out there?

Thanks in advance for patience with my n00bness,
Rob

---

### Post by geraldm on 2007-11-07
Hello Rob,
I took a quick look at the article mentioned.  It appeared to me to be creating an install file
for a keycode to glyph for use in typing.
Is the custom keyboard you are trying to use much different from the one in
[http://en.wikipedia.org/wiki/Image:KB_Russian.svg](http://en.wikipedia.org/wiki/Image:KB_Russian.svg)

I could be way off base on this, but I would have thought that there would be a 
Cyrllic font available, with the keycodes already set up, and a person would only have
to select a code page and font to use.  
Is your project ready with the icons to use, and the keycodes laid out, and awaiting the 
last step?
 I think the article is difficult to understand for someone who is not a programmer.
I will check into SCIM a little more.

Gerald

---

### Post by tbg58 on 2007-11-08
Thanks very much for your reply, Gerald.
Actually the keyboard in the linked graphic is a native Russian keyboard and what I'm not really able to use.  Russians touch type on that one.
The YaWerty keyboard supplied with Ubuntu looks like this one:
[http://www.m17n.org/common/m17n-docs-en/ru-yawerty.png](http://www.m17n.org/common/m17n-docs-en/ru-yawerty.png)
or pretty close at least.
Whereas the one I was used to using before looks a bit different, with most of the keys where they are on this one, but some minor differences - more similar to this one:
[http://www.cyrillic.com/cyrstart/scrshot.gif](http://www.cyrillic.com/cyrstart/scrshot.gif)
This was from a vendor I used to use back in the days when I was on Windows 95.  Microsoft had a layout editor for Windows 2000 and subsequent releases which created an install file.  I used that for school computers and my Windows machines, bur now that I have all my systems switched to Ubuntu (except one) I really wish there were something like that for SCIM.  If the SCIM project were in Python I might tackle it.  But it's not, and I'm not strong enough in C to do the job.
Fonts are really not a problem, as the unicode-compliant ones in Ubuntu already handle Cyrillic with no problem.  I can type in Russian using YaWerty, and the results are fine.  I just would prefer a layout like the one I've used for years -- just being stubborn, I suppose, but one of the way we get really great tools in the FLOSS world is by scratching our own itches.  
Thanks again for your reply.

Kindest regards,

Rob Mitchell

---

### Post by geraldm on 2007-11-08
Hello again.
I have been thinking that the SCIM project is quite a diversion from the goal.  SCIM has its
greatest value in the far eastern languages, where it takes many keystrokes to output a 
single character in, say, Chinese.  There are no project starts for any of the Russian-like
languages in that project, just oriental languages.

I also thought about keymaps, to be  used in X.  But that seems too complicated as well.

Another approach to be considered would be a plugin to an editor such as vim.  A user 
could have two xterm programs on the screen, and in one xterm be running the editor with
a plugin.  The plugin would translate any keys pressed into the Cyrllic characters for its 
display.  The other xterm program would be unaffected by the Cyrllic even if it was vim, but 
operating without the plugin.   

This last approach seems to be the simplest for me to understand, as the closest foreigners
to me are Canadians, and even those insulate from the French Canadien keyboard.  The 
U.S keyboard is too entrenched, and English seems to be quite dominant in the www, so 
I cannot envision being separated from the US glyphs and US keyboard for long.
Implementing a glyph translation seems to be to be a workable approach.

The translation idea would work for other keyboards shown on wikipedia, and it could also
function as a template for other keyboards and languages.  I just do not have a good 
understanding of how other natives are coping now.  I would be more tempted to think
that something like this must already have been done, and I am not finding it. 

In any event, I thought that there could be a project, with a license like the GNU free
documentation license, to implement the glyph translations.  I would need to look into
some ways of achieving it before formally beginning a project or effort.

Gerald

---

