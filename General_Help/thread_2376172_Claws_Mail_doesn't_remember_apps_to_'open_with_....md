---
title: "Claws Mail doesn't remember apps to 'open with ...'"
date: 2017-10-31
forum: General Help
---

### Post by amanchesterman on 2017-10-31
I have recently switched to Claws Mail from Thunderbird and I'm hoping that a more experienced user can help me. If this isn't the right forum please move this post.

I am running Xubuntu 17.04 and I installed Claws from the Software centre. In almost every respect it runs perfectly, there's just one feature (bug?) I find irritating: it doesn't remember which external app to use in order to open attached files.

Suppose I receive an email with a Word document attached, or a spreadsheet. When I press the hotkey 'O' or click on 'open', Claws correctly suggests an external application to handle the file (in my case, LibreOffice Writer or Calc) - I assume it gets that information from the Xubuntu environment. But if I select 'remember this' in the dialogue, it doesn't remember it: whether I then go to another email with that kind of attachment, or even back to the original email with the same attachment, each time Claws suggests the (correct) application and I have to agree to the suggestion before the application is launched.

I remember that Thunderbird also suggested external applications to handle such files, on first use; but there was an option in the dialogue to 'always use this application for this type of file' (or something like that), and once selected, Thunderbird didn't ask again. That's the kind of behaviour I'd like from Claws!

My version of Claws is 3.14.1. I have installed Clawsker, which lets you tweak various options and features of Claws, but it doesn't include anything about this aspect of its operation.

Thanks in advance for your help!

---

### Post by matthorton2 on 2017-10-31
someone here might know more?

[http://www.claws-mail.org/MLs.php?section=community](http://www.claws-mail.org/MLs.php?section=community)

---

### Post by amanchesterman on 2017-11-01
Thanks, good suggestion. I thought I'd try here first but now I'll ask them too.

---

### Post by amanchesterman on 2017-11-02
OK I worked it out. I'm posting the solution here in case anyone else is puzzled as I was; this doesn't seem to be covered in the Claws Mail documentation.

Claws Mail displays the various parts of a message separately, so the first step is to select the part which is the file attachment. (The various parts are displayed as icons beside the message reading pane.)
Then the **first** time you open an attachment of a particular file type, use the command View/Message part/Open with (or the hotkey, the default is O). A dialogue pops up suggesting an external application to handle that type of file. If you want this to be the default thereafter, tick the box 'remember this'.
Then in future, when you want to open an attachment of the same type, use the command View/Message part/Open (or the hotkey, default is L).

In this way you can set up different external applications to handle different kinds of attachments.
Of course, at any point you can use the 'open with' option, either to select a different application for a particular occasion, or to change the default application to use -- in the latter case, tick the 'remember this' box again.

I hope this helps someone!

---

