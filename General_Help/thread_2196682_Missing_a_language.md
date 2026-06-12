---
title: "Missing a language"
date: 2013-12-30
forum: General Help
---

### Post by John Jason Jordan on 2013-12-30
My old computer has Xubuntu 12.04 and in the language settings for the keyboard I was presented with three choices for Greek: Modern, Simple, and Polytonic. I selected Polytonic and it always worked flawlessly. My new, awesome my-winter-present-to-me computer has Xubuntu 13.10 and the only Greek keyboard option is Modern. I need the Polytonic keyboard. Where did it go? Am I missing a package? Searching Synaptic has not helped. I am in a hurry here, because classes start in one week! I am handicapped due to an injury to my hand and must depend on computers to produce legible homework. 

Any suggestions are welcome!

---

### Post by mörgæs on 2013-12-31
Did you try installing lxkeymap?

---

### Post by grahammechanical on 2013-12-31
Ok. After reading your post I downloaded and installed Xubuntu 13.10 with English as my default language. This is what i just did.

1) Clicked the Xubuntu icon = Applications menu
2) Selected Settings Manager and under the heading "Hardware" I clicked Keyboard
3) I opened the Keyboard Layout tab and I unticked the box "Use System Defaults."
4) I went into the Keyboard Layouts panel and I clicked Add ( + )
5) I scrolled down the list of keyboard layouts until I came to Greek
(6) I expanded the selection by clicking the arrowhead.
(7) I was presented with these options

Greek (eliminate dead keys)
Greek (extended)
Greek (polytonic)
Greek (simple)

I selected Greek (extended) and then Greek (polytonic) and clicked OK and then Close.

I next went back to System Manager and I selected Panel under the Personal heading. I followed that by

8) Opening the Items tab and
9) scrolling down the list until I could select Keyboard Layouts
10) I clicked the Add button ( + )

Now when I load into Xubuntu I see an Icon for keyboard layouts in the top panel (a UK flag actually) and in the drop down menu I get these options

gb (extd); gr (extended); gr (polytonic).

Why you do not get that I cannot say. I do not get options for modern. I can only guess that you are installing another Language option instead of a keyboard layout option. In fact it is in Language Support that I see a list of languages that includes - Greek, Modern (1453-). Perhaps you need to install the Greek, Modern, language option from Language support and then the Polytonic and Simple keyboard layouts from Keyboard to get that set up that you had in 12.04. Do not forget to add the keyboard layout icon to the top panel by using the Panel utility.

Regards.

---

### Post by John Jason Jordan on 2013-12-31
> **grahammechanical said:**
> 
1) Clicked the Xubuntu icon = Applications menu
2) Selected Settings Manager and under the heading "Hardware" I clicked Keyboard
3) I opened the Keyboard Layout tab and I unticked the box "Use System Defaults."
4) I went into the Keyboard Layouts panel and I clicked Add ( + )
5) I scrolled down the list of keyboard layouts until I came to Greek
(6) I expanded the selection by clicking the arrowhead.
(7) I was presented with these options


Thanks so much for your reply. I tried Mörgæs' lxkeymap suggestion, but it didn't help. What I had missed was:

(6) I expanded the selection by clicking the arrowhead.

Thjat's all I needed. It's working perfectly. But now I feel way too stupid to be studying Ancient Greek!

---

### Post by grahammechanical on 2013-12-31
Are you familiar with this site?

[http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:Greco-Roman](http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:Greco-Roman)

I use it to access the Liddell - Scott Greek-English Lexicon.

Regards.

---

### Post by John Jason Jordan on 2013-12-31
> **John Jason Jordan said:**
> That's all I needed. It's working perfectly. But now I feel way too stupid to be studying Ancient Greek!

I spoke too soon. The IBus keyboard chooser icon in the notification area now shows Ancient Greek, and right after I posted that it was working perfectly, it did work. But today, even though the chooser icon still says Ancient Greek, what I get is Modern Greek keyboard when I select it. Furthermore, the Onboard keyboard no longer changes from English to Greek when I choose the Greek keyboard. 

Also, I cannot get the hotkey keyboard changer to work. Previously I had it set to Ctrl-Shift, but that is no longer an option and none of the options in the GUI window actually work. There is a <space> in the window, and no explanation of what it is for. The GUI window has no Help button and I can't find any documentation.

---

### Post by John Jason Jordan on 2013-12-31
> **grahammechanical said:**
> Are you familiar with this site?
[http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:Greco-Roman](http://www.perseus.tufts.edu/hopper/collection?collection=Perseus:collection:Greco-Roman)
I use it to access the Liddell - Scott Greek-English Lexicon.

[off-topic:on]
Thanks for the link suggestion. I access the Liddell-Scott lexicon from the link on Thesaurus Linguae Graecae. 
[off-topic:off]

---

### Post by John Jason Jordan on 2014-01-02
I have had a terrible time trying to get English (default) and Greek polytonic keyboard on Xubuntu 13.10. I have to post this from a different computer becaue my computer is currentlystuck in Greek, and I cannot change it. Why? Because to delete the Greek keyboard I need my password, and my keyboard is currently in Greek, so it won't take the password. 

I need to delete or edit whatever files are involved in this, but bear in mind that i cannot type anything. I must do everything only with a mouse. Even in a terminal everything is in Greek. To delete or alter files I might have to boot to a Knoppix or something.

Desperate!

Edit: I managed to fix it. Now I have only US English. I need to reinstall polytonic Greek and get Onboard to work with it.

---

### Post by mörgæs on 2014-01-02
Please don't create multiple threads regarding the same problem.
Merged.

---

### Post by John Jason Jordan on 2014-01-02
I thought that the problem I had was different, but that is not important. 

At the moment I have reinstalled the polytonic Greek keyboard, along with English, and I can switch back and forth between them. However, Onboard only shows the English keyboard, regardless of which is currently selected. If I was in the Greek keyboard &#921; &#969;&#959;&#965;&#955;&#948; &#946;&#949; &#964;&#968;&#960;&#953;&#957;&#947; &#953;&#957; &#915;&#961;&#949;&#949;&#954;, as I just did. But Onboard remains in English.

On my old computer (Xubuntu 12.04) Onboard would immediately change when I switched input methods. Here on my new 13.10 computer it is permanently stuck in English. I've tried changing the settings, but nothing makes any difference.

Is it possible to make Onboard act the way it did on 12.04?

---

