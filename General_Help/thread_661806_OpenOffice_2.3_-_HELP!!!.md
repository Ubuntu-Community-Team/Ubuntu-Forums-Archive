---
title: "OpenOffice 2.3 - HELP!!!"
date: 2008-01-08
forum: General Help
---

### Post by jferreir on 2008-01-08
I just made the switch to Ubuntu 7.10 from XP and the transition has been a bit bumpy. I was under the impression that OpenOffice 2.3 was capable of reading most Microsoft Office documents, but there is definitely a problem!

1. I can't properly read '.doc' files:
When I open the average '03 word document, the formatting is incorrect; all the words are bunched together with no spacing, and there are a few foreign characters that appear. I have the mscorefonts installed, so I'm not sure what's causing this problem. When I try to open the document, I get a popup which is called 'ASCII Filter Options'- what is this and why is it popping up? I have yet to open a normal file without any problems...

2. I can't find additional fonts:
Although the mscorefonts package is installed, there are very limited fonts to choose from. There MUST be additional font packages somewhere, but I can't seem to find any, and even if I do, I don't know how to install them. I'm used to 'book antiqua' from Word...

3. I can't make '.docx' files compatible:
I found an article which describes how to make OpenOffice compatible with '.docx' files, but being the noob that I am, I can't follow simple instructions. Can someone please translate these steps into an idiot proof guide?? I managed to complete the first step, but that's it. Here is the link:
[http://www.sigmundvoid.com/?p=81](http://www.sigmundvoid.com/?p=81)

I've tried searching everywhere and this is my last ditch effort... PLEASE HELP!!!

---

### Post by 50words on 2008-01-08
I am not sure why you are having trouble with .doc files. I get very few compatibility issues. I think your first impulse--that it could be font-related--could be correct, but it could be a result of the Word features used to format the .doc files. I have found OOo --> Word compatibility to be better than Word --> OOo.

On the fonts, open up Synaptic rather than Add/Remove Programs and search for "font". You will get a lot of options. You can also use TrueType fonts by typing fonts:/// in any file browser window, which will open up the fonts folder. Just drag .ttf font files into that folder, and you can install them. If you still have your Windows partition, you might just want to copy over all your Windows fonts to ensure you have them.

You can also download free fonts. I like urbanfonts.com, which has a wide variety of free fonts available.

As for .docx files, I think OOo is probably still having issues because the .docx format is so new. Your best bet is to re-save them as .doc files. Since so many people are still using Word 2003, everyone should be willing to re-save as .doc at this point, and the compatibility issues will hopefully be resolved by the time .docx becomes more widely used, assuming that happens.

---

### Post by tech9 on 2008-01-08
you could try to read your docs with a program called antiword... should be in the repos

---

