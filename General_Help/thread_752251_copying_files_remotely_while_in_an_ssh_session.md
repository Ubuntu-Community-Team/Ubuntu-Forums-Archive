---
title: "copying files remotely while in an ssh session"
date: 2008-04-11
forum: General Help
---

### Post by Rizla on 2008-04-11
I know i can use scp for this, but I was wondering how you'd go about copying a file on my remote server to my local system while i'm already in my ssh session to the server.

I'm currently logged in via ssh, i tried doing scp <filename>  but that didnt seem to work.  

Is this even possible, i'm guessing not..

---

### Post by Rizla on 2008-04-11
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, so i decided to just do it via standard scp like so

```

scp -P <myshhport> <username>@<serverip>:/media/nasdrive1/THE\ FILE\ I\ WANT.pdf .

```

the second part of that is where i'm getting hung up, i'm trying to transfer a file that has white spaces in it.  Hence the backslashes, but i get the error that the 'THE' directory doesnt exist.  Is there a escape key i need to prefix the filename to transfer files with spaces?

BTW, i'm going to get rid of white spaces in my files names in the future becuase its a pain in the CLI.

EDIT:
[b] Fixed it.  I had to encapsulate the filename with an apostrope '  and it worked.  Also, i had a mistake in my path to the file, so that was the first issue.  DUH... me=sofa king ...

---

### Post by fsmithred on 2008-04-11
I don't think there's a way to do that, but I could be wrong. How I get around it is to either open another terminal and use sftp (or scp), or, if it's a text file and not too big, view it with less or cat and copy/paste to a local text editor.

---

### Post by Rizla on 2008-04-11
**This post could be related to an Ubuntu bug filed at**: > **WW said:**
> No worries.  If we all read all the manuals before asking a question, there would be no one here.  Not because we'd know all the answers, but because we'd all have been bored to death. [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **fsmithred said:**
> I don't think there's a way to do that, but I could be wrong. How I get around it is to either open another terminal and use sftp (or scp), or, if it's a text file and not too big, view it with less or cat and copy/paste to a local text editor.

how do you copy the text on a command line?

---

### Post by fsmithred on 2008-04-12
In gnome-terminal, you can use the mouse to select text, then right-click for a menu that includes copy/paste. Sometimes ctrl-insert, shift-insert works when right-click doesn't.

---

