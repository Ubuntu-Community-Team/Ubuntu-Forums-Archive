---
title: "I want to kill Docbook"
date: 2008-05-13
forum: General Help
---

### Post by minaev on 2008-05-13
Docbook is not for work. First, it's awkward. Even an XML dialect could be less prolix. I was really surprised that ISO, NIST and Russian ministry of heavy industry are not the only bodies able to produce a standard that takes seven lines to insert a screenshot:

```
<screenshot>
   <mediaobject>
    <imageobject>
      <imagedata fileref="qwerty.png" format="PNG"/>
    </imageobject>
  </mediaobject>
</screenshot> 
```

Okay, I know there could be only five lines, but why five if one is enough?

And the culmination of the docbook spirit. Ta-da! The first place goes to the tag <confsponsor>. I really miss <cellphoneofconfsponsorsprettiestdaughter>.

Second, Docbook toolchain is next to non-existent. Docbook-utils require a half-dead jadetex. Xmlto requires a completely dead passivetex. Two xsl:fo formatters: Java-based dinosaur fop (not in Ubuntu repositories) and the newborn xmlroff, which has two backends, neither of which was able to produce a readable text on my files. And Dblatex, which "just works", and produces the results it wants, but not the results I need.

And the last point. "You can concentrate on the content and forget about the presentation," say the proponents of Docbook. No, guys, I can't. Because if I give a manuals written in Docbook to my customers, I will lose my job. I **have** to think about presentation. Some days ago I needed to make a pdf for a 3.5"x4.5" screen (eInk device) with the font a couple of points smaller than usual. Guess how much time it required? Two hours. And the last 15 minutes I spent reformatting the text in OOo.

Now, let's talk in a constructive way. What are the alternatives? I just want to:

1. write short (<50 pages) instructions, policies and manuals with images, tables and hyperlinks;

2. be able to render them as pdf, rtf and html (at least);

3. easily change the presentations styles: fonts, justification of level 2 headlines, color of hyperlinks, etc.

Am I asking too much?

---

### Post by minaev on 2008-05-13
At a Russian Linux forum I received the following advices:

[LIST]
[*]DITA (rejected for the same reasons as Docbook)
[*]markdown + pandoc
[*]Emacs Muse (I like it, but it's a different class of applications, like markdown)
[*]reStructuredText (reST)
[*]txt2tags
[/LIST]

Not too much, but I have also found two other interesting alternatives: Lout and Z Format. The former seems very interesting, but it'll take some time before I make my mind. The latter has no documentation and almost no description. But these 3 lines of description are intriguing :).

---

