---
title: "Libre Office THESAURUS"
date: 2016-10-25
forum: General Help
---

### Post by ray42 on 2016-10-25
Recent install of Gnome.

My Libre office thesaurus was greyed out, why? I found the solution to my problem I think. 

[http://extensions.libreoffice.org/extension-center/english-dictionaries/releases/2016.05.01](http://extensions.libreoffice.org/extension-center/english-dictionaries/releases/2016.05.01)

I looked for a long time to find this. Do the dictionaries and thesaurus not get auto update?

Update:
The previous page no longer works, try the new page:
[https://extensions.libreoffice.org/extensions/english-dictionaries/2017-01.01](https://extensions.libreoffice.org/extensions/english-dictionaries/2017-01.01)

---

### Post by Buntu Bunny on 2016-10-26
The thesaurus for LibreOffice can be found in Synaptic Package Manager. The file's name is 

mythes-en-us 

(or the language of your choice). In Synaptic do a search for "thesaurus" and you'll find it to mark for installation.

---

### Post by ray42 on 2016-10-31
I live in the United Kingdom, is that the correct one?

---

### Post by oldrocker99 on 2016-10-31
> **ray42 said:**
> I live in the United Kingdom, is that the correct one?

There isn't a specific UK thesaurus, but the USA one should do just fine; there is also an Australian one, **mythes-en-au**.

---

### Post by Buntu Bunny on 2016-10-31
> **ray42 said:**
> I live in the United Kingdom, is that the correct one?

You'll want 

**mythes-uk**

If you do a search in Synaptic for LibreOffice thesaurus, a list of mythes files will come up. UK is the last one on the list.

Do you have Synaptic Package Manager installed? If not you can find in in the Software Center.

---

### Post by ray42 on 2016-10-31
> **Buntu Bunny said:**
> You'll want 

**mythes-uk**

If you do a search in Synaptic for LibreOffice thesaurus, a list of mythes files will come up. UK is the last one on the list.

Do you have Synaptic Package Manager installed? If not you can find in in the Software Center.

Yes, it does but it tells me that is "Ukrainian Thesaurus for LibreOffice"

---

### Post by Buntu Bunny on 2016-10-31
> **ray42 said:**
> Yes, it does but it tells me that is "Ukrainian Thesaurus for LibreOffice"

Oh my! The jokes on me for that one, LOL. The moral of the story is never make assumptions.

oldrocker99 is correct then and you have a choice of US or AU for an English thesaurus. Australian spelling will be closer to British spelling, so if it was me, I'd go with that one.

---

### Post by ray42 on 2016-11-22
Hmm, some time later.....

After following my own theory here is what I have found. Yes the English Thesaurus is available! WHAT! Take a look for yourself at the pic uploaded.

[ATTACH=CONFIG]272299[/ATTACH]

---

### Post by Buntu Bunny on 2016-11-24
Well done, ray42. It's always a good feeling to solve your own problems, isn't it?

---

### Post by nicnok on 2017-03-15
> **ray42 said:**
> Hmm, some time later.....

After following my own theory here is what I have found. Yes the English Thesaurus is available! WHAT! Take a look for yourself at the pic uploaded.

[ATTACH=CONFIG]272299[/ATTACH]

Mod: Sorry to niggle but this 'solved' Q is incomplete. I followed the instructions in this Q but got nowhere. The above link proves a UK thesaurus is available but omits to say how to get it: ie what it's called in Synaptic [or if not in Synaptic how to obtain it]

---

### Post by Buntu Bunny on 2017-03-15
Does this help?

> 1) Remove the US dictionary hunspell-en-us (but not the core hunspell spellchecker):
$ sudo apt-get remove hunspell-en-us

2) Install a GB dictionary – hunspell is backwards compatible with myspell, they use the same format:
$ sudo apt-get install myspell-en-gb

Notice that it actually installs the dictionary in /usr/share/hunspell, not /usr/share/myspell/dict – presumably because it recognises that we’re using hunspell (it’s installed) not myspell (it isn’t) as the spellcheck engine. Instead it puts links into the myspell directory for compatibility.

3) That’s it. Keep mythes-en-us (or install it if necessary: $ sudo apt-get install mythes-en-us) because it does actually include GB spellings (you can grep the files for colour, theatre, specialise, etc), and as long as the symbolic links to the non-existent GB thesaurus files (as in step 3 above) are in the directory, Libreoffice will recognise it, and will show Hunspell (UK) and Thesaurus (UK) modules enabled in Tools -> Options -> Language settings -> Writing aids.

You can view the original (and full) blog post [here]("http://www.astarix.co.uk/2012/06/proper-british-language-tools-libreoffice/").

---

### Post by nicnok on 2017-03-17
Mod: [you may wish to simplify this post or adjust BB's?] 
Sorry to niggle again & sorry to be pedantic: > **Buntu Bunny said:**
> 3) Keep mythes-en-us ........ as long as the symbolic links  to the non-existent GB thesaurus files (as in step 3 above) are in the  directory, Libreoffice will recognise it, and will show Hunspell (UK)  and Thesaurus (UK) modules enabled in Tools -> Options -> Language  settings -> Writing aids

I followed the advice in the previous post but it still left me with a greyed-out 'Thesaurus Ctrl+F' in 'Tools> Language'. I was not until I re-read the detailed advice in the usefully provided link that I realised that > **Buntu Bunny said:**
> 3) ...as long as the symbolic links  to the non-existent GB thesaurus files (as in step 3 above) are in the  directory ....  is vital. To repeat that [nicely detailed, thanks!] step 3 it is:
> **the link to www.astarix.co.uk said:**
>  3. Finally, create symbolic links between the en-us and non-existent en-gb versions so that Libreoffice sees them.
 $ cd /usr/share/mythes/
$ sudo ln -s th_en_US_v2.idx th_en_GB_v2.idx
$ sudo ln -s th_en_US_v2.dat th_en_GB_v2.dat 

By the by I have to confess to installing the suggested files via Synaptic rather than Terminal.

All working well now - many thanks!

---

