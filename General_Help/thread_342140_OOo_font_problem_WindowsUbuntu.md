---
title: "OOo font problem Windows/Ubuntu"
date: 2007-01-19
forum: General Help
---

### Post by OrangeCrate on 2007-01-19
I use OOo on both Dapper and my WinXP Home partitions.

Prior to installing Ubuntu, I used Bookman Old Style on Windows for my business letterhead. After installing Dapper, I installed the MS font pack from the repositories. It didn't have Bookman, but there is a similar font called URW Bookman L. As an alternative to Bookman Old Style, I have been using URW Bookman L. No problem using this font when creating a PDF file, but apparently there is with a MS Word document.

By chance, I just found out, that the URW font does not render correctly when viewed in OOo on Windows, and therefore I would assume that there would be the same problem if someone is using MS Office.

Is there be an additional font pack that I'm not aware of that would pickup Bookman Old Style on Ubuntu, or is there a workaround solution to this? I'd hate to change the font after all of these years. It's almost like a "brand" now. Any help would be appreciated.

Thanks.

---

### Post by OrangeCrate on 2007-01-20
Bump.

---

### Post by rigol on 2007-01-20
Did you try to mark your text and just type the font's name there where you can choose the font? For university I have to type in Times New Roman and this isn't in the list also, but manually typed in OO I can use it.:confused:

---

### Post by OrangeCrate on 2007-01-20
Rigol,

Thanks for the suggestion. I tried it typing in Bookman and Bookman Old Style, and it in fact changed the font on the highlighted text, but not to Bookman. Looks more like Verdana.

As I mentioned, I can use URW Bookman L in OOo on Ubuntu with no problems, but when you try to read the document on Windows, it ends up looking like Verdana. Usually I'm pretty good at figuring out these little puzzles, but this one has me stumped. The simple answer of course is to just change the font on my letterhead, but for the reasons mentioned in my original post, I'd like to try to keep it.

Searching on Google doesn't give me a hint, so I thought that someone here might have experienced a similar problem. I've also posted this question on the OOo forum, but no one there appears to have an answer either.

---

### Post by mcduck on 2007-01-20
Do you have the 'URW Bookman L' installed in Windows too?

---

### Post by OrangeCrate on 2007-01-20
^,

No I don't, and I do understand that would solve the problem for me to view it in my windows partition. But, that doesn't address the big picture.

My primary concern is the people I communicate with in my business. I send memos and letters often as attachments, and unless they specifically had URW Bookman L installed, I will have lost the font on my letterhead (both header and footer) when they view the document.

The puzzle I'm trying to solve here, is to use a Bookman style font in OOo on Ubuntu, that windows users will be able to immediately see as if nothing is different.

I think the answer is to find the MS Bookman Old Style font and install it on Ubuntu. But, as mentioned, I find no reference on google, or anywhere else for a font pack, or instructions to add just that font.

Thanks for your response, it's appreciated.

---

### Post by mcduck on 2007-01-20
The font's are not included in word documents like they are in PDF files, so you need to always use a font that you know people reading the document have. So if you want windows users to be able to see the documents the way you did them, you need to use a font you know all windows users have. 

If you believe that all windows users you want to read that document also have the 'Bookman Old Style' font, and you have that font in Windows, you could just copy it to your Linux. Otherwise I recommend sticking to basic windows fonts like Arial, Verdana or Times New Roman. Most people at least have those.

---

### Post by OrangeCrate on 2007-01-20
> **mcduck said:**
> you have that font in Windows, you could just copy it to your Linux.

That's the answer I've been trying to find. Would you happen to know how I would copy the font on my windows partition, and then install it on my Linux partition? If so, that solves my problem.

---

### Post by OrangeCrate on 2007-01-20
^^,

The lightbulb just went off. Had my brain stuck on trying to find another font file, rather than just grabbing the font from Windows. A stick did the trick.

Learned something new mcduck, thanks for the help.

---

### Post by mcduck on 2007-01-20
No problem. I was actually struggling with the same problem, and in the end decided to just send PDF files when ever possible, and otherwise just use Arial font.

---

### Post by OrangeCrate on 2007-01-20
^,

O.K., since you're experiencing the same problem, let me expand on what I did. After you mentioned just copying the file, the lightbulb went off, and I searched again, and found the initial solution here:

[http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html](http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html)

But, rather than all the fonts, I just wanted one for now, so, I went to the windows font file, and sent the font I wanted to a USB flash stick. I removed the stick, and rebooted into Ubuntu. I then installed the stick, and dragged the font to the desktop. I then opened the System font file, and dropped in the font from the desktop. When I opened OOo, low and behold, there it was. I checked that it worked with an email attachment sent from Ubuntu and opened in windows. Worked perfectly.

---

### Post by mcduck on 2007-01-20
> **OrangeCrate said:**
> ^,

O.K., since you're experiencing the same problem, let me expand on what I did. After you mentioned just copying the file, the lightbulb went off, and I searched again, and found the initial solution here:

[http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html](http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html)

But, rather than all the fonts, I just wanted one for now, so, I went to the windows font file, and sent the font I wanted to a USB flash stick. I removed the stick, and rebooted into Ubuntu. I then installed the stick, and dragged the font to the desktop. I then opened the System font file, and dropped in the font from the desktop. When I opened OOo, low and behold, there it was. I checked that it worked with an email attachment sent from Ubuntu and opened in windows. Worked perfectly.

Like I said earlier, I usually work out these little puzzles pretty quickly, but this time I got vapor locked. Again, thanks for your help.
Thanks, but I actually meant that I have already solved the problem by only using PDF's or fonts that I know most people have, whatever operating system they are using. In the end there's no other way to do it if you don't know what fonts other people have installed.. (doesn't really matter anyway, there's usually no need for those people I send files to be able to edit them in any way so PDF documents work just fine.

---

### Post by OrangeCrate on 2007-01-20
^,

Got it. Unlike you, I often need to have clients edit stuff, so .doc files are a big part of my practice, though I do use .pdf documents for "policy" matters too.

Your point about knowing what other fonts people use is certainly valid. I take the leap of faith that my clients have Bookman Old Style, since virtually all of them are using a version of MS Office. (Actually, I don't know of one client that uses OOo.)

---

### Post by Mguel on 2008-06-23
I got to the same problem with needing Bookman Old Style font for Open Office (I'm using Kubuntu 8.04 hardy heron with KDE 3.59). I read this thread, but what I finally made was even easier:

I browsed to the font folder on windows partition, identified Bookman Old Style font, right clic -> Actions -> Install. And you're done!

Very nice and easy.

Cheers.

PS: wanted to post even it being an old thread since it may help someone else (considering this thread appeared on the top results at google when I searched).

---

