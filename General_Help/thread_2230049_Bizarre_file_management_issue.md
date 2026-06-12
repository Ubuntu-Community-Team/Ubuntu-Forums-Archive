---
title: "Bizarre file management issue"
date: 2014-06-17
forum: General Help
---

### Post by craig10 on 2014-06-17
Hi there,

Of all the things I thought I might run into in transitioning from one OS to another, I didn't think file management issues would be one of them.

I am trying to move some files from one directory to another on the same drive. Files with the same names exist in the destination directory. The files I am trying to move have been mass modified using sed. When I try to move the files, Nautilus of course complains that a file of the same name exists in the destination directory. So I select "Apply this action to all files" and then click the "Replace" button. There seems to be activity for a brief second and then the operation is done.

Or is it? Oddly, the files have not been moved because they're still there in the source directory.

So I go to the destination directory and the files that should have been overwritten are still there with their old modification timestamps. When I open the files to see if they reflect the changes made by sed, they do not. They are still the old unmodified files.

I own both the modified files and the destination files that should be overwritten. The latter are readable and writable by me. I tried moving just one file, but with the same result.

What on earth could be going on here?


Craig

---

### Post by deadflowr on 2014-06-17
Sometimes things are circumstantial.
It would be helpful to know the sed command used and the other OS.

---

### Post by craig10 on 2014-06-17
Hi Deadflowr,

Thanks for your reply. I may have confused the issue with my reference to transitioning from one OS (Windows XP) to Ubuntu. I stopped using XP about two months ago, so this issue is not related to the transition.

As for the sed command, it's not related either. The command was run on the files in the directory and did what it needed to do successfully. Trying to move the files was a manual operation after the fact. But if you really want to know:

```
find ./*.php -type f -exec sed -i 's/StringToReplace/ReplacementString/' {} \;
```


Craig

---

### Post by dragonfly41 on 2014-06-17
In your previous OS - Windows XP - you were probably familiar with the two pane utility Total Commander which makes batch file copying/moving very easy in a GUI.

The equivalent file management tool I use in Ubuntu is Krusader .. found in Ubuntu Software Centre.

There are other two pane tools such as Double Commander but my personal choice is Krusader.

If you wish to use Krusader in root mode go to Tools > Start Root Mode Krusader.

See if you get different results using Krusader..

---

### Post by craig10 on 2014-06-17
Hi Dragonfly,

Thanks for your reply. While I never used Total Commander with XP, I vaguely remember using a Norton tool (Norton Commander?) back in the Windows 95 days that was a DOS-based, twin-pane file manager. But I can't honestly say I'm "familiar" with Total Commander or one of the "Commander" file managers. Although I thought there had to be something better, I just muddled along with Windows Explorer.

Anyway, I did what I needed to do with Terminal (without using sudo), although I still can't explain the weird behaviour of Nautilus.

And using mv in Terminal made me realise that it behaves differently than it does in Red Hat and CentOS; under those it confirms overwrites by default, but under Ubuntu mv overwrites without confirmation by default. Wasn't thrilled about that, but I didn't lose anything irreplaceable.


Craig

---

### Post by Impavidus on 2014-06-18
To have **mv** prompt you before overwriting a file, use the -i option. Other Linuxes may set up an alias that includes the -i option by default, which you can override with -f.

---

### Post by craig10 on 2014-06-18
Hi Impavidus,

Thanks. Yes, CentOS and Red Hat do alias "mv" to "mv -i". I'll be setting that up too. It's what I'm used to and what I prefer.


Craig

---

