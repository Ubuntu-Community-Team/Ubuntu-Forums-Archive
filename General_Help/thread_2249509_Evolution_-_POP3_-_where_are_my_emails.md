---
title: "Evolution - POP3 - where are my emails ?"
date: 2014-10-22
forum: General Help
---

### Post by kevin119 on 2014-10-22
I am new to Ubuntu and Evolution. 

I created a mail account on Evolution with POP3 account and SMTP. 

Now I am trying to restore my emails. 

How can I get my emails back ?

Thx,

Kevin

---

### Post by Steven_Williams on 2014-10-22
Can you explain more about what happened with your emails? Was Evolution working at all after you set it up? Did it die suddenly? We will need more information in order to help you.

Unless you made sure to turn this setting off POP3 normally deletes emails off the server once it puts them on your computer. You can turn this off, but unless you made sure to do that that would be why you can't get them off the server. This is one reason I prefer using the IMAP protocol instead. Is the Ubuntu install where you had Evolution still working?

---

### Post by buzzingrobot on 2014-10-22
If you collected mail with another mail client before using Evolution, then, as Steven says, it's most likely the case that those emails were deleted from the server.  Evolution *should* fetch any new mail. (If you can, try sending a test message to that account.) 

In any case, the POP standard is to remove mails from the server when they are downloaded.  Some services, including Gmail, I believe, allow that deletion to be optionally delayed for a period of time.

---

### Post by kevin119 on 2014-10-24
All the emails were in Microsoft Outlook. Now after receiving via Evolution POP3 account, those emails from Outlook are gone. 

Now my question is where are those emails downloaded ? Under what file extension ? And how can I retrieve/see  those emails back into evolution ?

Please help.

---

### Post by lisati on 2014-10-24
Was Outlook set up with IMAP or POP? If Outlook downloaded your mail with POP3, there is a strong possibility that your emails were deleted from the server, so Evolution won't be able to pick them up.

The usual process for POP3 is that it copies the mail from your provider's computer to your computer, and then arranges for the deletion of the copy stored on your email provider's system.

---

### Post by kevin119 on 2014-10-24
Yes outlook was setup with POP. I saw downloading message after POP account was set up. But where can I find my downloaded emails ?

---

### Post by nerdtron on 2014-10-24
Not sure if Evolution can import the outlook emails but here's the link too backup the emails on pop outlook [http://www.howto-outlook.com/howto/backupandrestore.htm](http://www.howto-outlook.com/howto/backupandrestore.htm)

---

### Post by buzzingrobot on 2014-10-24
> **kevin119 said:**
> Yes outlook was setup with POP. I saw downloading message after POP account was set up. But where can I find my downloaded emails ?

Mail downloaded with Outlook will be in the folders Outlook uses.  Unless you can import it into Evolution, Evolution won't know it's there.

*New* mail downloaded with Evolution will, of course, be in the folders Evolutions uses.

Unless Outlook offers an option to delay deletion of POP mail at the server, and you have chosen that option, then any POP mail retrieved from Outlook servers by *any* client -- Outlook, Evolution, etc. -- will be deleted from the servers as soon as it is downloaded to your system.

Evolution displays the current mail accounts in a panel on the left of its display.  By default, you should see the account you created, with the name you gave it, and an "On This Computer" account (which can be disabled), as well as "Search Folders", where search results can be displayed.

---

