---
title: "[SOLVED] How do I have a name randomly picked and then removed from a list in Spreads"
date: 2008-05-05
forum: General Help
---

### Post by Rytron on 2008-05-05
Hi,
I got the text below from a webpage. I cannot get it to work in Open Office Spreadsheets. The text below are for excel so maybe there is a subtle difference that is causing it not to work in Open Office Spreadsheets.
I want to have a list of names. Then I need to have a name randomly picked and then removed from the list. Kind of like taking names out of a hat.

I'd be delighted if someone could show me how to get this to work. 

Thanks.

[B]> But what if you have a list of names and you want to select one at random? It easier than you may think! Follow these simple steps;

   1. Enter a list of names in column A
   2. Now enter the formula below in the cell you want the random name returned.

=INDEX($A:$A,RANDBETWEEN(1,COUNTA($A:$A)),1)

This will pick a name at random from your list in column A. It will also be dynamic in that when/if you add/remove names from the list they will automatically be included/excluded.

If you have a table of data (more than 1 column) and you wish to select an item at random from the table, you could use:

=INDEX($A:$C,RANDBETWEEN(1,COUNTA($A2:$A65536)),RANDBETWEEN(1,3))

This assumes your table 3 columns wide, hence; $A:$C and RANDBETWEEN(1,3) and we do not want row 1 includes as it contains headings, hence; COUNTA($A2:$A65536)[/B]

---

### Post by erginemr on 2008-05-12
Hello Rytron,

I think I have found a way do it. Please experiment with the attached file. I didn't figure out the removal part. But this will at least give you a head start.

Take care. :)

---

### Post by Rytron on 2008-05-12
> **erginemr said:**
> Hello Rytron,

I think I have found a way do it. Please experiment with the attached file. I didn't figure out the removal part. But this will at least give you a head start.

Take care. :)

Hi erginemr,
You are a star. I'm not certain as to exactly how to use it yet. I change the content of A7 and press enter to get a random name at B7. What should I change the cell A7 content to - anything? I will try to figure out more of it. Very cleverly done. Cheers my friend.

:)

---

### Post by erginemr on 2008-05-12
You are most welcome. :p

Yes, I put it there for you to change it at your heart's content, because otherwise, the randomize function wouldn't renew itself. 

Deleting the selected name would prove to be a difficult task though. I think both random selection and deletion can be only be done with a macro, which is bound to a button. So, you would press the buttton to both renew the selected item, and also delete the name in the selected list. The problem is; this is beyond my lore, so you'll have to mess with macro recording / editing.

May I ask what your avatar is? It seems extremely familiar. :roll:

Cheers.

---

### Post by Rytron on 2008-05-13
> **erginemr said:**
> You are most welcome. :p

Yes, I put it there for you to change it at your heart's content, because otherwise, the randomize function wouldn't renew itself. 

Deleting the selected name would prove to be a difficult task though. I think both random selection and deletion can be only be done with a macro, which is bound to a button. So, you would press the buttton to both renew the selected item, and also delete the name in the selected list. The problem is; this is beyond my lore, so you'll have to mess with macro recording / editing.

May I ask what your avatar is? It seems extremely familiar. :roll:

Cheers.


Thanks. The avatar I use is from the good old [Commodore 64]("http://en.wikipedia.org/wiki/Commodore_64"). By the way is that avatar you use a [Patterdale Terrior]("http://en.wikipedia.org/wiki/Patterdale_Terrier")? My grandmother has a Patterdale and he looks very similiar to your avatar. Cheers.

---

### Post by Rytron on 2008-05-13
what does Çal&#305;&#351;ma Sayfas&#305;1 mean? it is the title of sheet 1 of your spreadsheet that you uploaded here. cool writing (Turkish).

---

### Post by erginemr on 2008-05-13
Commodore of course! Stupid me! :KS

I am not sure about the breed of my avatar, but chances are it may be a Labrador:
[http://en.wikipedia.org/wiki/Labrador_Retriever](http://en.wikipedia.org/wiki/Labrador_Retriever)

Sure it has a noble air, I wish I had such a dog.

"Çal&#305;&#351;ma Sayfas&#305;" is the Turkish for "SpreadSheet". You have a keen eye, there. :rolleyes:

Take care mon ami.

---

### Post by Rytron on 2008-05-14
> **erginemr said:**
> Commodore of course! Stupid me! :KS

I am not sure about the breed of my avatar, but chances are it may be a Labrador:
[http://en.wikipedia.org/wiki/Labrador_Retriever](http://en.wikipedia.org/wiki/Labrador_Retriever)

Sure it has a noble air, I wish I had such a dog.

"Çal&#305;&#351;ma Sayfas&#305;" is the Turkish for "SpreadSheet". You have a keen eye, there. :rolleyes:

Take care mon ami.

Yes, I'd say you are right he is most likely a Labrador.
I have since come across this handy site. Here is a link to its list randomiser: [http://www.random.org/lists/]("http://www.random.org/lists/")
Slán (goodbye in Irish)
:)

---

