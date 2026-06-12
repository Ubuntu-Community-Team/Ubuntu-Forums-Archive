---
title: "Searching within a man page for the term firewire"
date: 2012-11-04
forum: General Help
---

### Post by zee220 on 2012-11-04
Hey guys!

I installed ubuntu 12.10 on virtual pc, and tried to find the term 'firewire' in a particular man page by typing ' / firewire' however I keep getting the message 'pattern not found'.

Does anyone know the correct way to do this? first i type man man to get into a man page, and then I type '/ firewire', which is basically 'searching within a man page', or am I missing something?

Help would be highly appreciated.

Thanks!

---

### Post by codemaniac on 2012-11-04
> **zee220 said:**
> Hey guys!

I installed ubuntu 12.10 on virtual pc, and tried to find the term 'firewire' in a particular man page by typing ' / firewire' however I keep getting the message 'pattern not found'.

Does anyone know the correct way to do this? first i type man man to get into a man page, and then I type '/ firewire', which is basically 'searching within a man page', or am I missing something?

Help would be highly appreciated.

Thanks!

man generally uses the less terminal pager.
When yo uare doing a /*serchpattern *, to jump through the results, press N (forwards) and Shift+N (backwards).

---

### Post by zee220 on 2012-11-04
Thank you for your response. I apologise for my lack of knowledge, but I don't think it answered the question for me. Would you say, the way I am trying to find the term firewire within a man page is correct?

If not, what is the correct way to search within a man page in the terminal.

Thanks

---

### Post by JKyleOKC on 2012-11-04
Omit the space after the "/" and it should work. With the space, you're looking for " firewire" and that may not be anywhere to be found.

Also, case is important. You may need to try "/Firewire" also...

---

### Post by zee220 on 2012-11-04
I've tried many variations

/firewire

/ firewire

/Firewire

/ Firewire

Still nothing :(

---

### Post by stinkeye on 2012-11-04
Best way I've found is to install man2html...
```
sudo apt-get install man2html
```

Add
```
http://localhost/cgi-bin/man/man2html
```
to your Firefox bookmarks and use the browsers page search.

---

### Post by Cheesemill on 2012-11-04
Which man page are you looking at?

Does it actually contain the word firewire?

---

### Post by codemaniac on 2012-11-05
> **zee220 said:**
> I've tried many variations

/firewire

/ firewire

/Firewire

/ Firewire

Still nothing :(

**/firewire**
should work if the keyword **firewire **exists in the manpage you are searching. Please also note the whole *nix thingy is case sensitive and fireware ,Fireware,FireWare all are different patterns .

---

### Post by Habitual on 2012-11-05
```
man -k <keyword>
```

[http://manpages.ubuntu.com/manpages/hardy/en/man4/firewire.4.html](http://manpages.ubuntu.com/manpages/hardy/en/man4/firewire.4.html)

---

