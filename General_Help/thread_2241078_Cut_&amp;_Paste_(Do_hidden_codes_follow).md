---
title: "Cut &amp; Paste (Do hidden codes follow?)"
date: 2014-08-24
forum: General Help
---

### Post by suomalainen on 2014-08-24
Hello Ubunteros,

if a person writes 'something' using gedit of libre office and then cuts & pastes whatever it was they wrote into a Thunderbird email to send to someone, what hidden 'codes' are also transfered during the cut & paste process that was performed?

Thank you!

Suomalainen

---

### Post by vasa1 on 2014-08-24
> **suomalainen said:**
> Hello Ubunteros,

if a person writes 'something' using gedit of libre office and then cuts & pastes whatever it was they wrote into a Thunderbird email to send to someone, **what hidden 'codes'** are also transfered during the cut & paste process that was performed?

Thank you!

Suomalainen
Do you mean formatting?

---

### Post by suomalainen on 2014-08-24
You question is too complicated. I mean exactly as I stated.

---

### Post by suomalainen on 2014-08-25
bump...

---

### Post by mcduck on 2014-08-25
It depends. Gedit is a pure text editor, so the only "hidden codes"  would be the usual hidden characters, like spaces, tabs, line changes etc. and those of course are included when you copy/paste the text.

LibreOffice is a bit more complicated, as it's formatting options go beyond pure text. Depending on your settings in Thunderbirdthe text you copy/paste will either end being pasted as pure text (loosing any formatting), or it gets converted into HTML (in which case the only "hidden codes" carried over would be those that can be turned into HTML tags to format the text to look same it did in LibreOffice). You can always use the "Other Actions"->"View Source" to check all the contents of a message. (I can't remember if the option is available when writing a message, but if it isn't, saving it as a draft should allow you to view it)

---

### Post by suomalainen on 2014-08-25
Thanks for the feedback.

It is my understanding that by not writting an email directly into the email editor and instead following the method I listed above, may cause emails to go directly into ones junk mail folder.

Thanks!

---

### Post by mcduck on 2014-08-25
Shouldn't make any difference, but e-mail spam filters tend to be more strict about HTML mails, so if you want to be sure just set Thunderbird to default to plain text mails instead. That way everything you paste into the message will be converted to plain text, even if you copy/pasted it from a rich text editor or word processor such as LibreOffice Writer.

---

### Post by pqwoerituytrueiwoq on 2014-08-25
paste something from libreoffice into thunderbird and press [Ctrl]+[A] then open the 'Insert' menu and click on 'HTML' in the menu, then you will see the 'hidden' codes
in this window a traditional line break will not show up unless it is contained within '<pre></pre>' tags otherwise a line break will appear as '<br>'

---

