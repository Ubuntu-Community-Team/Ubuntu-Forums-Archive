---
title: "can someone explain to me all these different theme types?"
date: 2008-04-22
forum: General Help
---

### Post by uschxc on 2008-04-22
I've googled and wiki'd around but haven't really found a clear cut answer.  

as far as i know i'm running avant windows manager on top of compiz fusion, which is on top of gnome.

but when i goto gnome-look.org for example i see metacity, which i apparently also use, gtk2.0, which i think i use, beryl and compiz which are merged into compiz fusion as far as i understand.

so i'm trying to figure out how metacity, gtk, and the compiz themes stack up.  it seems gtk themes change window decorations and gnome-panel stylings while metacity just changes the decorations but i'm interested to know how they tie in to each other, or how they are layered, or if they are redundant.

i'd like a pretty desktop but utilizing the fewest programs to do so.  awn + compiz fusion + some theme that will change windows decorations + the gnome panel decoration.

---

### Post by theCroc on 2008-04-22
Compiz and beryl themes are only if you use the old theme managers for compiz and beryl. (Like emerald) These are as far as I know discontinued but some ppl still use them. 

Metacity handles your windowborders. If you are running Compiz then Metacity isn't running. 

This is where it can get a bit blurry. GTK 2+ handles all visual UI elements (Buttons, checkboxes, scrollbars etc.) as well as windowborders. So what you want is GTK2+ themes. 

I hope that cleared things up a little bit. As far as I know you can still use metacity themes even if you are running Compiz. But that only changes the borders and titlebar.

In your case I would go with just using GTK themes.

/Michael

---

### Post by uschxc on 2008-04-22
i believe you can run metacity and compiz fusion together, i used to have the gnome-compiz-manager or whatever package which had the option of enabling desktop effects (which requires compiz i believe) and enabling metacity themes.  the metacity switch would just remove the default ubuntu theme (metacity/gtk i'm pressuming here?) when unchecked and display a softer skin which i'm guessing was the compiz fusion skin.  i haven't been able to get emerald skins to work actualy.  i have themes loaded and such but they never get drawn.  i wonder if metacity is drawing over them?  

but yea i need to get this all straightened out.

---

### Post by charlemagne86 on 2008-05-22
> **theCroc said:**
> Compiz and beryl themes are only if you use the old theme managers for compiz and beryl. (Like emerald) These are as far as I know discontinued but some ppl still use them. 

Metacity handles your windowborders. If you are running Compiz then Metacity isn't running. 

This is where it can get a bit blurry. GTK 2+ handles all visual UI elements (Buttons, checkboxes, scrollbars etc.) as well as windowborders. So what you want is GTK2+ themes. 

I hope that cleared things up a little bit. As far as I know you can still use metacity themes even if you are running Compiz. But that only changes the borders and titlebar.

In your case I would go with just using GTK themes.

/Michael
Emerald is obsolete????!!!!

I am not sure but i was under the impression that it was the new thing....and also if those vista-ish looks n all are old them GOd knows what is new....

Either get you facts straight or guide me to the required reading material....

Sorry for bein rude, if i am, but u just turned my world upside down in a single post!!


cheerios

---

### Post by mcduck on 2008-05-22
> **charlemagne86 said:**
> Emerald is obsolete????!!!!

I am not sure but i was under the impression that it was the new thing....and also if those vista-ish looks n all are old them GOd knows what is new....

Either get you facts straight or guide me to the required reading material....

Sorry for bein rude, if i am, but u just turned my world upside down in a single post!!


cheerios

No, Emerald is not obsolete. It's just that Ubuntu, by default, used CGWD instead becasue it uses same themes that the default window manager in Gnome, Metacity, does.

And no, you can't run Metacity and Compiz at the same time. Only one window manager can  be running at any time. But, like I said, Compiz has several dfferent window decorators (programs it uses to draw different types of window themes), and these include ones that are able to use Metacity and Kwin themes..

---

### Post by Forlong on 2008-05-22
> **charlemagne86 said:**
> Emerald is obsolete????!!!!
"theCroc" said (as far as he/she knows), it's discontinued, not obsolete. And that is pretty much accurate. Emerald is mostly unmaintained and doesn't really get developed any further.

Btw: Emerald is two years old, as is Vista's look. I do call that old in terms of desktop design.

---

### Post by charlemagne86 on 2008-05-24
Oops...my bad...

okay okay...so emerald is discontinued...thanks for the info guys..


so what is it succeeded by?? or what is the latest in the desktop designing front?

---

