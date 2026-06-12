---
title: "Libreoffice Base doesn't show wizard when creating subform"
date: 2014-04-12
forum: General Help
---

### Post by Lotiopep on 2014-04-12
Hello everybody.

When Ubuntu 14.04 beta was released I installed it and started woking with it. I created a new Libreoffice database with multiple tables and forms. I'm pretty new to Libreoffice Base. But now I'm very confused because when creating a subform inside a form which will display the fields of another table there is no wizard prompted asking for the fields you want to include in the subform table. I'll try to explain step by step:

1. Edit form that displays a single table content.
2. Click on "form navigator" => Right click on "main form" => "new" => "Form"
3. Right click on the new form created (inside "form navigator") => "Properties"
4. Then I fill "Content type" with "table", in "content" I choose the table name I want to display, then I click on "link master fields" and choose the fields that relates both tables.
5. And now, having the subform selected, click on "more controls" => "table control" and I create a framework (using the mouse) in orther to make the new table fields appear, but.... the wizard that should let you choose the fields you want to include doesn't appear. Instead, it appears the table without any field. 

After that, I have to include manually all the fields.

I would swear that it worked fine when I created a previous form with three subforms so, as I said, I'm very confused.
I opened the same database in Windows and it worked fine. Then I thought it was because of the Libreoffice version included in Ubuntu 14.04 Beta (4.2.3) so I removed it and installed the version 4.2.2, but the wizard wasn't prompted as it did in Windows with same version of Libreoffice. Then I decided to install Elementary OS Luna and install Libreoffice 4.1.5.3, but it happened the same than in Ubuntu.

I have searched for an answer in google but could't find any posts related to this (maybe because I have to make a search for this problem in english and I don't do it properly).

I attach screenshots reproducing the problem in a new test database.

So... does anybody know what is happening? Can you help me?

Thank you for your help.

---

### Post by amanchesterman on 2014-04-12
This is quite a specialised question. You **may** find someone here who can answer it directly, but you may have better luck asking it in one of the forums dedicated to Base. (I have used Base a bit myself, but I have not needed to use sub-forms so I have not personally faced your problem.)

There is a lot of helpful advice on the Open Office forum. In particular, there is a good tutorial here:
[https://forum.openoffice.org/en/forum/viewtopic.php?f=83&t=28235](https://forum.openoffice.org/en/forum/viewtopic.php?f=83&t=28235)
It explains how to create forms and sub-forms in Base and it has links to other sources of help. You could also try posting your question (as above) in the Base forum, there are some real experts there.

Don't be put off by the fact that that is the 'Open Office' rather than the 'Libre Office' support forum. OO and LO are still quite similar packages (I believe they were originally the same) and the Base component in particular is almost identical in my experience of it.
The Libre Office forum offers advice on Base here:
[http://en.libreofficeforum.org/node/5872](http://en.libreofficeforum.org/node/5872)
However you will see that some of the sources they recommend are in the Open Office forum.

I hope this helps!

---

### Post by Lotiopep on 2014-04-13
Thank you for your answer. I will try to post the question in the libreoffice forum.

---

