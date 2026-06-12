---
title: "Tool for deleting e-mail attachments"
date: 2008-01-01
forum: General Help
---

### Post by 50words on 2008-01-01
Is there a way to remove or delete attachments from an e-mail in Evolution? I have not been able to find any option to do this. I use IMAP, if it matters.

If not, is there a tool to remove or delete attachments in batches. I use IMAP size ([http://www.broobles.com/imapsize/](http://www.broobles.com/imapsize/)) in Windows for this, but I can't find anything similar in the repos. Is there a CLI option?

(I know there is an extension for Thunderbird to do this, but I don't use Thunderbird and don't want to switch to it just to delete an attachment, then switch back to Evolution. Using Thunderbird is not an option, as I need a PIM, not just an e-mail program, and Sunbird/Lightning does not cut it.)

---

### Post by knattlhuber on 2008-01-03
I was looking for the same thing. A Google search brought up this plugin:

[http://people.debian.org.tw/~chihchun/2006/10/23/remove-attachments-plugin-for-evolution-001/]("http://people.debian.org.tw/~chihchun/2006/10/23/remove-attachments-plugin-for-evolution-001/")

There are no binaries and no make file... you have to put the plugin into the Evoution source tree and compile it. I haven't tried (or shall I better say: dared?) to do that, so I don't know if it works.

---

### Post by 50words on 2008-01-03
Yeah, that looks promising but scary. Guess I'll stick with IMAPsize in VirtualBox.

---

