---
title: "I would like an explanation please"
date: 2007-11-05
forum: General Help
---

### Post by ardchoille42 on 2007-11-05
I use libdvdcss with MPlayer to watch DVD movies that I have purchased. I never copy a DVD movie and I am the only one who watches them on my Ubuntu computer. I have had people tell me this is illegal in the US. My question is .. "why is it illegal?" I've asked that question of many people but no one has ever given me an explanation. The reason I asked "why" is because I have found too many times in life that people will repeat what they hear without ever researching whether or not it is true.

Today, I found this article:
[http://www.osweekly.com/index.php?option=com_content&task=view&id=2689&Itemid=449](http://www.osweekly.com/index.php?option=com_content&task=view&id=2689&Itemid=449)

I went to the LinDVD website to see if I could download and install LinDVD - which would be legal because it is a viable commercial alternative. The first thing I read on their website was this:

"LinDVD, InterVideo's Linux software DVD player, is currently available only to manufacturers for evaluation and integration."

And this sentence is in red lettering:
"[COLOR="Red"]Available only to manufacturers[/COLOR]"

So, the only viable commercial alternative to libdvdcss is not available to Linux users. If there isn't a viable commercial alternative, why us it illegal to use libdvdcss?

Can someone please provide an explanation (with proof/documentation) as to why it is illegal to use libdvdcss in the United States?

If using libdvdcss isn't illegal, then we need to get it into the official repos and let the public know the truth.

I don't want this to turn into a flame war, I just feel that the Linux community deserves to know the truth.

---

### Post by jpeddicord on 2007-11-06
It is technically illegal because of a bunch of things, the main one being the DMCA by the US Govt. The DMCA covers CSS, an encryption scheme used to keep unauthorized players from reading any DVDs. libdvdcss' existence is legal, however using it for anything other than "research purposes" is where it becomes illegal, as it is clear you are trying to get around the CSS encryption.

Proprietary players that have CSS obey specific parts of the DMCA to restrict what the user can do with the DVDs.

Basically, it is illegal because libdvdcss doesn't restrict what you can do, and it contains source for anyone to unencrypt a DVD.

If I'm wrong, someone correct me. I've got a general sense of this, but it's not something I've looked into with much depth.

---

### Post by ardchoille42 on 2007-11-07
> **jacobmp92 said:**
> It is technically illegal because of a bunch of things, the main one being the DMCA by the US Govt. The DMCA covers CSS, an encryption scheme used to keep unauthorized players from reading any DVDs. libdvdcss' existence is legal, however using it for anything other than "research purposes" is where it becomes illegal, as it is clear you are trying to get around the CSS encryption.

Proprietary players that have CSS obey specific parts of the DMCA to restrict what the user can do with the DVDs.

Basically, it is illegal because libdvdcss doesn't restrict what you can do, and it contains source for anyone to unencrypt a DVD.

If I'm wrong, someone correct me. I've got a general sense of this, but it's not something I've looked into with much depth.

From what I understand, using libdvdcss is only illegal if it needs to implement DeCSS to allow for encrypted DVD viewing.. and I don't think libdvdcss implements DeCSS. Is it possible to prove that DeCSS decryption had taken place in DVD viewing anyway?

It's illegal to use DeCSS but the MPAA has never said anything about libdvdcss.

Quote: [MPAA.org]("http://www.mpaa.org/dvd_faq.asp")
[I]Q. Doesn't the DMCA allow reverse engineering for compatibility, for example to allow playing of a DVD on a Linux operating system-driven personal computer? 

A. The DMCA does allow reverse engineering. However, the reverse engineering provisions in the DMCA were never intended to enable anyone to circumvent technical protection measures (TPMs) for the purpose of gaining unauthorized access to or making unauthorized copies of copyrighted works.[/I]

The key word here is "unauthorized". I'm not attempting to do anything that is unauthorized, what I am doing is fully authorized (viewing a DVD that I have purchased). In a courtroom, the prosecution must prove intent to commit a crime and I don't see how they can do that when what I am doing is "authorized" according to their own definition.

From the MPAA:
*The DMCA does allow a lawful user of a computer program to circumvent TPMs to ensure that the program can work with other programs (interoperability); and, with strict limitations, the research may be shared with others, as long as it does not infringe the copyright in the original or a related work. However, reverse engineering is not permissible if there is a readily available commercial alternative for that purpose.*

There are no readily available commercial alternatives for Linux users (LinDVD is not available to the public).

Still searching for an answer.

---

