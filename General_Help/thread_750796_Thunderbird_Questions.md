---
title: "Thunderbird Questions"
date: 2008-04-09
forum: General Help
---

### Post by Complete on 2008-04-09
I have two thunderbird questions.

When I use Thunderbird to import my address book, it does not ask where 
to look to import the file.  Is there some special place I need to put my 
outlook express file for the thunderbird software to find it?

In the faq of webmail ( [http://webmail.mozdev.org/faq.html](http://webmail.mozdev.org/faq.html) ) they have 
the question of how to install these extensions but you say "In 
Mozilla Thunderbird, open the extension manager (Tools Menu/ 
Extensions)".  But I do not see any such place in the tools menu.

---

### Post by drs305 on 2008-04-09
> **Complete said:**
> 
In the faq of webmail ( [http://webmail.mozdev.org/faq.html](http://webmail.mozdev.org/faq.html) ) they have the question of how to install these extensions but you say "In Mozilla Thunderbird, open the extension manager (Tools Menu/ Extensions)".  But I do not see any such place in the tools menu.

In the linux version extensions are found in Tools, Add-Ons. In the lower right there is a link to "Get Extenstions".

Here is a link about importing emails for OE to Thunderbird. It is a year old but may still be helpful.
[http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution](http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution)

---

### Post by Complete on 2008-04-10
> **drs305 said:**
> In the linux version extensions are found in Tools, Add-Ons. In the lower right there is a link to "Get Extenstions".

Here is a link about importing emails for OE to Thunderbird. It is a year old but may still be helpful.
[http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution](http://www.howtoforge.com/importing_outlook_express_into_thunderbird_evolution)

This does not work because the machine I am setting up is notthe machine that had Outlook Express.

---

### Post by drs305 on 2008-04-10
I believe the link provided would have you install Thunderbird on the same machine as Outlook Express. You then follow the instructions to transfer the OE files over to Thunderbird. Once you have that accomplished, you can copy the Thunderbird profile over to your linux machine.

---

### Post by Complete on 2008-04-10
> **drs305 said:**
> I believe the link provided would have you install Thunderbird on the same machine as Outlook Express. You then follow the instructions to transfer the OE files over to Thunderbird. Once you have that accomplished, you can copy the Thunderbird profile over to your linux machine.

OK.  Good idea.  I am doing this.  Which files make up the Thunderbird profile -- the files I need to copy over.  I have managed to install Thunderbird on the older machine and import all the OE settings and files.

---

### Post by drs305 on 2008-04-10
I use swiftdove, which is an offshoot of thunderbird. However, I believe the thunderbird profiles, by default, are located in /home/USERNAME/.thunderbird.  Note the . which means it's normally a hidden file. You may have to alter your file manager to display it (view hidden files). You can put the profile wherever you desire but that is where the default profile is stored. Each default profile will have an odd combination of letters and numerals. If you create your own, you can name it something more reasonable.

To create a new profile (I don't recall using Caps, but on the mozilla help sheet it's:
```
thunderbird -ProfileManager
```

---

