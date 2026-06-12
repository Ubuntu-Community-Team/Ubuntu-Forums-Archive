---
title: "copy entire contents from vi editor on to clipboard"
date: 2015-05-27
forum: General Help
---

### Post by IAMTubby on 2015-05-27
Hello,
 I am working by ssh'ing onto a remote server using putty and so vi is the only software I have at my disposal.

I would like to copy the entire contents of a text file from this server on to my local computer. Assuming I cannot scp the file, and the only way I can do this is by copying and pasting, how can I copy all the contents from this file on to the clipboard, so I can paste on to my local system.

I have tried the following, but wasn't successful.
```
gg"+yG
```
```
[FONT=Consolas]:%w !pbcopy[/FONT]
```

---

### Post by 1clue on 2015-05-27
ssh and scp are the same server, same protocol.  If you can edit it in vi then you can scp it.

Failing that, there are command line tools like pastebin which might be helpful, designed to copy entire files.

---

### Post by SeijiSensei on 2015-05-27
I usually just highlight all the text, right-click to choose Copy, then Paste it into the destination.  For longer files, you'll need to repeat this until you've captured the whole file.

---

### Post by ajgreeny on 2015-05-27
> **SeijiSensei said:**
> I usually just highlight all the text, right-click to choose Copy, then Paste it into the destination.  For longer files, you'll need to repeat this until you've captured the whole file.
In vi (or nano)?

Surely you can't do that in the cli editors, or if you can, I am not aware of it, nor how it can be done.

---

### Post by Habitual on 2015-05-27
```
ssh user@host cat  /etc/rsyslog.conf  > ./woof.txt
``` is what I do, where "ssh user@host" are dozens of hosts.
and I heavily use aliases for rapid access to remote hosts, so ```
<host_alias> cat /some/file > ./here.local
```
shoots me in and out and done.

---

### Post by SeijiSensei on 2015-05-28
> **ajgreeny said:**
> In vi (or nano)?

Surely you can't do that in the cli editors, or if you can, I am not aware of it, nor how it can be done.

My method uses the native copy/paste functions of the Terminal client.  While I use Konsole (KDE), I'd be surprised if you can't highlight and copy text from other graphical terminal clients as well.

---

### Post by ajgreeny on 2015-05-28
> **SeijiSensei said:**
> My method uses the native copy/paste functions of the Terminal client.  While I use Konsole (KDE), I'd be surprised if you can't highlight and copy text from other graphical terminal clients as well.
You may be correct, but if so I can still not figure out to do it in nano, the cli editor I use, and apart from telling me to use command **nano -m** to enable mouse use, **man nano** does not help me.

---

### Post by SeijiSensei on 2015-05-29
No, you cannot do it from within nano or any other text editor.  They have no way to communicate to X and the desktop environment.  You need to use the standard Copy/Paste functions built into the desktop environment, in particular those found in the GUI Terminal app itself.  Unless you're running in pure text-mode (like at the recovery console), you're using nano within a Terminal window, right?

Try painting the text with your mouse, then right-click on the highlighted text.  Can you choose Copy?  How about if you highlight the text and choose Edit from the Terminal window menu?

---

### Post by ajgreeny on 2015-05-30
I tried painting the text in nano with the mouse and it did not highlight text or do anything.

I then had a bit of a brainstorm and read **man nano** in more detail; I had set an alias for nano using **nano -B -S -m -$** without realising that the mouse enablement when using the -m option was not what I thought it should be; it simply allows you to place the cursor by clicking in the text, but it removes the ability to highlight text and use the copy/paste from right click.

So, my problem is solved, and I have to accept that it was my own fault; a result of me trying to be clever, but messing up what already was possible if I did not use the -m option for nano.

---

### Post by 1clue on 2015-05-31
I haven't actually tried any of this but I can think of a couple ways you might do this from inside vim.  The caveat is that you scp the saved version of the current file back to your workstation.  You would need ssh server running on your workstation.

So for example you could do something like:
```

who am i | sed 's/^\(\S*\)..*(\(.*\))/\1\@\2/'

```

You'll get you@your-ip-address, but only if you're logged in remotely.  Likewise in vim tips here [http://vim.wikia.com/wiki/Get_the_name_of_the_current_file](http://vim.wikia.com/wiki/Get_the_name_of_the_current_file) say that you can get the current filename being edited fairly easily.

It seems to me that with a bit of experimentation you could:
```

:!scp <something-from-the-vim-tips-website> `who am i | sed 's/^\(\S*\)..*(\(.*\))/\1\@\2/'`

```

The only serious loophole here is that this assumes you have the same login name on both boxes.  And that your client is reachable by ssh at the reciprocating address (so not if you're behing a nat firewall for example)

The key being of course that all this is much harder than opening a second terminal from your client box, and 
```
scp you@remote_host:/path/to/file ~/Downloads/file
```

Just saying, if you can ssh over and edit the file then you can absolutely positively scp it from the same box.  ssh and scp are the same protocol.

---

### Post by kjohri on 2015-05-31
I do this for contents of vi buffer, SSH terminal etc. The downside is that you need to do this multiple times, typically one screen or less at a time. Just click mouse, keep the mouse button pressed and drag the mouse. This paints the selected text. Then, right click to get menu and click Copy. This copies the selected text into clipboard. You can paste the copied text in some other application.

---

