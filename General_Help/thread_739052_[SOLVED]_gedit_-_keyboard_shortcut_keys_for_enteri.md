---
title: "[SOLVED] gedit - keyboard shortcut keys for entering ascii characters"
date: 2008-03-29
forum: General Help
---

### Post by bw44 on 2008-03-29
Can I create keyboard shortcuts in gedit for ascii characters that don't appear on my keyboard keys, like the British pound sign and the em-dash?

I know about using the Applications>Accessories>Character Map to find the Unicode sequences for the characters, but it's pretty cumbersome to type CTL+Shift+U2014 to produce an em dash.  I'd like to be able to assign, say CTL+m or CTL+ (keyboard dash), and use that instead.  Is it possible?

Thanks.

---

### Post by mcduck on 2008-03-29
Have you tried the Alt Gr key (or right Alt)? At least on all Scandinavian, and US international, keyboard layouts you can use Alt Gr combined with different keys to get quite a large selection of special characters.

[http://wiki.linuxquestions.org/wiki/Accented_Characters]("http://wiki.linuxquestions.org/wiki/Accented_Characters")

---

### Post by y-lee on 2008-03-29
Gedit has a plugin, Snippets,  which is capable of doing what you wish. 

In gedit click Edit and then Preferences and then the Plugins tab, be sure Snippets is checked. Now close the preferences windows. 

Now to create your own snippets in gedit click Tools and then Manage Snippets. In this window click New and in the edit Snippet text area create your snippet ( for your example type Ctrl-Shift-U2014) and in the Accelerator text area type the keypress you wish to associate with this snippet (Ctrl + m say). 

Close this window and test it. Worked for me :lolflag:

---

### Post by bw44 on 2008-03-29
> **mcduck said:**
> Have you tried the Alt Gr key (or right Alt)? At least on all Scandinavian, and US international, keyboard layouts you can use Alt Gr combined with different keys to get quite a large selection of special characters.

[http://wiki.linuxquestions.org/wiki/Accented_Characters]("http://wiki.linuxquestions.org/wiki/Accented_Characters")
Thanks very much for the suggestion.  I don't think my keyboard has an Alt Gr key and the right Alt does not seem to work as described on the page for which you gave the link.  But I have bookmarked it for future reference.

---

### Post by mcduck on 2008-03-29
> **bw44 said:**
> Thanks very much for the suggestion.  I don't think my keyboard has an Alt Gr key and the right Alt does not seem to work as described on the page for which you gave the link.  But I have bookmarked it for future reference.

According to Wikipedia both Canadian International and Canadian French keyboard layouts should have Alt Gr key. Have a look at keyboard settings and if there are other Canadian layouts thatn the one you are now using try if one of them works correctly with the Alt Gr/right Alt key.

edit: also make sure that the keyboard settings have been set to use keyboard with right number of keys. Using a 104-key setting with 105-key keyboard for example would result to one key not working, and this often seems to be the AltGr..

---

### Post by bw44 on 2008-03-29
> **y-lee said:**
> Gedit has a plugin, Snippets,  which is capable of doing what you wish. 

In gedit click Edit and then Preferences and then the Plugins tab, be sure Snippets is checked. Now close the preferences windows. 

Now to create your own snippets in gedit click Tools and then Manage Snippets. In this window click New and in the edit Snippet text area create your snippet ( for your example type Ctrl-Shift-U2014) and in the Accelerator text area type the keypress you wish to associate with this snippet (Ctrl + m say). 

Close this window and test it. Worked for me :lolflag:Thanks very much for this.  I would never have discovered it unless someone pointed to it!

I think something may have changed since the version of Ubuntu/gedit you're using.  I have attached a screen shot of the Snippet Manager page. I can't make out what the "Tab trigger" field is for, Here's the Snippet Help page description:> Tab Trigger                    

Enter the tab trigger for the snippet. This is the text that you type before pressing Tab to insert the snippet.                    

The tag must be either a single word comprising only letters, or any single character. The Tab trigger will highlight in red if an invalid tab trigger is entered.I've tried entering a number of things in the field, but nothing seems to happen. (Except whatever I put in is listed in the parentheses before the Ctrl+M beside "em-dash" in the left panel.) I can't figure out what the Tab trigger function is supposed to do. Is it an alternative to the shortcut key, or does it have something to do with "activating/deactivating" the snippet?

I'm also puzzled by how the "Drop targets:" field is used.  The drop down menu contains things like "text," , "text/plain," "text/xml," and "image/jpeg."  This field isn''t described in the Help page, which I find more than a little frustrating.  Any thoughts on this?

However,  it has done the job of getting an em-dash inserted with Ctl+m, and that's a great help.

Thank you again!

---

### Post by mcduck on 2008-03-29
THe tab trigger is separate from the shortcut. you can configure both, or just one of them

For example I use the snippets plugin for coding XHTML. I have a snippet for the "background"-tag and to use it I have set the tab trigger to "background", and no keyboard shortcut. To use the snippet when coding I just write "background" and press Tab.

So, snippets can be activated either by typing a keyword and pressing tab, or by pressing some specific keyboard shortcut.

You can also add many different snippets to the same keyword/shortcut. Then, when activated, you'll get popup list where you can select the snippet you want.

---

### Post by y-lee on 2008-03-29
> I think something may have changed since the version of Ubuntu/gedit you're using. I have attached a screen shot of the Snippet Manager page. I can't make out what the "Tab trigger" field is for,

Hmm yep I am running an older version of gedit and your screen shot looks a bit different. And I have no "Drop targets" menu item there. Trying to wait till Hardy comes out and update from dapper to hardy then :) 

Anyway I see if i can figure out the tab trigger thing later today, i gotta go somewhere now. And btw today was the first time i actually used the snippet thing in gedit, i knew about it but i use gvim for any serious editing i do and emacs for lisp stuff.

Regardless tho I suppose the snippets solved your problem :) and for the record I can't get the  Alt Gr/right Alt key thing to work with gedit either ... I put it on my list of stuff to figure out later, I'm sorta new to linux too so  that list is getting a bit long :lolflag:

Edit: Thanks  mcduck for the tab trigger stuff :)

---

### Post by bw44 on 2008-03-29
> **mcduck said:**
> According to Wikipedia both Canadian International and Canadian French keyboard layouts should have Alt Gr key. Have a look at keyboard settings and if there are other Canadian layouts thatn the one you are now using try if one of them works correctly with the Alt Gr/right Alt key.

edit: also make sure that the keyboard settings have been set to use keyboard with right number of keys. Using a 104-key setting with 105-key keyboard for example would result to one key not working, and this often seems to be the AltGr..Thanks for the follow-up post.  As far as I know I'm using the default (American) English keyboard setting.  The machine was purchased in the U.S. and I have not changed any of the keyboard settings (not knowingly anyway!)  The keyboard model is Generic 105-key (Intl) PC and the Layout is U.S. English according to the Preferences>Keyboard>Layouts control panel.

What does the Alt Gr key look like? Is it Green? :) I see from the Wikipedia page it always seems to be in where th right alt key is.  Both alt keys look and seem to function the same way on my machine.   My laptop is a Compaq Presario and it has a lot of keys marked with numbers or icons I don't know the meaning of.  I'd rather not change the keyboard layout unless I really know what I'm doing, so I will have to study your suggestion further.

Thanks again.

---

### Post by mcduck on 2008-03-29
> **bw44 said:**
> Thanks for the follow-up post.  As far as I know I'm using the default (American) English keyboard setting.  The machine was purchased in the U.S. and I have not changed any of the keyboard settings (not knowingly anyway!)  The keyboard model is Generic 105-key (Intl) PC and the Layout is U.S. English according to the Preferences>Keyboard>Layouts control panel.

What does the Alt Gr key look like? Is it Green? :) I see from the Wikipedia page it always seems to be in where th right alt key is.  Both alt keys look and seem to function the same way on my machine.   My laptop is a Compaq Presario and it has a lot of keys marked with numbers or icons I don't know the meaning of.  I'd rather not change the keyboard layout unless I really know what I'm doing, so I will have to study your suggestion further.

Thanks again.

In that case you need to use the US International layout instead of the normal US layout for the Alt Gr functionality.

Alt Gr is in the same place where Right Alt would be, it just says "Alt Gr" on the key instead of "Alt". But it makes no difference what is printed on your keyboard, when using the right layout the key will work as AltGr anyway.

(AltGr is short for Alternate Graphics)

---

### Post by bw44 on 2008-03-29
> **y-lee said:**
> Hmm yep I am running an older version of gedit and your screen shot looks a bit different. And I have no "Drop targets" menu item there. Trying to wait till Hardy comes out and update from dapper to hardy then :) 

Anyway I see if i can figure out the tab trigger thing later today, i gotta go somewhere now. And btw today was the first time i actually used the snippet thing in gedit, i knew about it but i use gvim for any serious editing i do and emacs for lisp stuff.

Regardless tho I suppose the snippets solved your problem :) and for the record I can't get the  Alt Gr/right Alt key thing to work with gedit either ... I put it on my list of stuff to figure out later, I'm sorta new to linux too so  that list is getting a bit long :lolflag:

Edit: Thanks  mcduck for the tab trigger stuff :)Yes, my thanks to ** both** you and mcduck!  You've answered my questions faster than I can ask them!  Mcduck's requirements for alternate keyboard layouts and controls are a lot more sophisticated than mine.

And I **would** wait for Hardy!  I went from Feisty to Gutsy and have struggled with a number of things that didn't work as well under the newer version. I hope Hardy is a little better tested and more stable.  But then I am fairly new to Linux and Ubuntu, so maybe  the problems have been mostly mine.

---

### Post by bw44 on 2008-03-29
> **mcduck said:**
> In that case you need to use the US International layout instead of the normal US layout for the Alt Gr functionality.

Alt Gr is in the same place where Right Alt would be, it just says "Alt Gr" on the key instead of "Alt". But it makes no difference what is printed on your keyboard, when using the right layout the key will work as AltGr anyway.

(AltGr is short for Alternate Graphics)This and your previous post have been really helpful (sorry I can't quite keep up -- trying to test).  From the way it's described in the Snippets Manager it sounded to me as if you entered tab and then the word.  The popup for the field says: "Single word with which the snippet is activated after pressing tab" (pressing tab then entering  the word obviously didn't do much -- duh!).  Now I  see how it works.

I'm going to read up on the US International layout to make sure I know what to suspect from different keys.  Once I remember changing keyboard layouts under Windows and chaos followed!  I'm sure your suggestion is good, but I want to look before leaping.  As it is, Snippets provides me with two ways of making a keyboard shortcut and AltGr will provide a third.  My cup runneth over!

Thanks again for your help!

---

