---
title: "winmail.dat, get rid of them, how?"
date: 2016-08-23
forum: General Help
---

### Post by yonnie on 2016-08-23
I get these paper-clips showing something attached to my email and I go to open the email and discover it's a worthless winmail.dat!  How can I configure Thunderbird to automatically delete these winmail.dat attachments so I see attachments that are useful and or needed?

---

### Post by oldos2er on 2016-08-23
Ask whoever's sending you RTF email to use plain text instead, assuming you want their communication. I don't know of a way to have Thunderbird auto-delete such mail, but you could create a filter to move them to a Junk or Spam folder if unwanted.

---

### Post by yonnie on 2016-08-23
I belong to several lists, can't ask half the planet to fix their email.  It's just seems easier if there was a way to trim off the attachment.

---

### Post by SeijiSensei on 2016-08-24
Do you have control over the server that receives your mail?  If so, you might be able to do some massaging with procmail.  If not, then using filters in TBird to move such messages into a separate folder is the only option.

If you're receiving these messages from listservers ("lists" as you call them), apparently the list administrators are not stripping attachments before redistributing the messages.  I manage a number of lists and routinely strip all attachments from messages.  Otherwise people who get the digested version of the list would see enormous blocks of MIME-encoded text in the middle of the file.  That also protects against people who want to send a document to the listserver that might be read by just one or two other subscribers.

Update: I may have spoken too soon.  Perhaps this add-on for TBird offers a solution: [https://addons.mozilla.org/en-US/thunderbird/addon/attachmentextractor/](https://addons.mozilla.org/en-US/thunderbird/addon/attachmentextractor/)

---

### Post by oldos2er on 2016-08-24
Have you tried talking to the list owners? Not sure what more you can do.

---

### Post by yonnie on 2016-08-26
I'm going to try the plugin, thanks.  

The problem with complaining about attachments is that they are useful, winmail.dat is useful for nothing and shouldn't even exist.  
The lists I receive contain code or photos for equipment, eliminating all attachments would generate a problem for all of the users.

---

