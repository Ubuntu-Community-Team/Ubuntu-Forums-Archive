---
title: "rsyn with --exclude option and ssh option"
date: 2024-09-25
forum: General Help
---

### Post by Old Jimma on 2024-09-25
Hello Ubuntuers:

I've been using this command to back-up files on "mini" to "thinkpad" computers:
> 
rsync -av -e ssh  mini@192.168.1.227:/home/mini/Documents/ 


I'd like to exclude the directory /home/mini/Documents/computer on mini@192.168.1.227 from being copied to "thinkpad"


is this the correct command:
> 
rsync -av -e --exclude 'mini@192.168.1.227:/home/mini/Documents/computer'    ssh  mini@192.168.1.227:/home/mini/Documents/ 


Thanks,
Old

---

### Post by ActionParsnip on 2024-09-25
Just to check, is this pulling from the remote system?
You could make this easier by mounting the SSHFS, then its a simple folder sync using the mount point :)

---

### Post by TheFu on 2024-09-25
> **ActionParsnip said:**
> Just to check, is this pulling from the remote system?
You could make this easier by mounting the SSHFS, then its a simple folder sync using the mount point :)

The problem with a local mount like this is that rsync doesn't use the network-aware mode that made it famous and will just copy everything again, like it was local storage.  In short, don't use sshfs.

Also, ssh has been the default transfer mode for rsync for multiple decades now. No need to specify it.
However, you do need to specify the target. The command only has the source.

```
$ rsync -avz --exclude **/Documents/computer     mini@192.168.1.227:Documents/    /some/place-for-the-backups/
```

Don't be afraid of whitespace.
Using the mini login will set the PWD to the ~mini HOME directory. No need to fully specify it.
Definitely set the target for the copied files.  You want any scripted command to run safely from any directory on your computer, right?

---

### Post by Old Jimma on 2024-09-25
Thank you, ActionParsnip. I'll investigate this.

To answer your question, in the parlance used in the documentation, my "client" is pulling from the "servers."

In the parlance you've used, I consider the remote system to be wha the documentation calls a "server."

---

### Post by Old Jimma on 2024-09-25
Hi The Fu:

I tried:
>  
rsync -av -e --exclude mini@192.168.1.227:/home/mini/Documents/computer  mini@192.168.1.227:/home/mini/Documents/ 


and got the error message 
[QUOTE] 
ssh: connect to host 192.168.1.227 port 22: No route to host
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code  at io.c(231) [Receiver=3.2.7]
[QUOTE] 

The easy solution to my problem is I will the make the directory transfered from the server to the clent will be identical to the directory contents of the computer folder in the client,

---

### Post by Old Jimma on 2024-09-25
Hello The Fu:

**Thought you'd enjoy knowing that when remote computers are turned off (because somebody working a vacuum cleaner cleaned up the power cable), rsync will not work under any circumstance.**

Do you think this could be some sort of bug?

---

### Post by TheFu on 2024-09-25
> **Old Jimma said:**
> Hi The Fu:

I tried:
```
 rsync -av -e --exclude mini@192.168.1.227:/home/mini/Documents/computer mini@192.168.1.227:/home/mini/Documents/ 
```

and got the error message 

ssh: connect to host 192.168.1.227 port 22: No route to host
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code  at io.c(231) [Receiver=3.2.7]


The easy solution to my problem is I will the make the directory transfered from the server to the clent will be identical to the directory contents of the computer folder in the client,

Lots of issues with that command. Lots.

 rsync -av[COLOR="#FF0000"] -e --exclude [/COLOR]mini@192.168.1.227:/home/mini/Documents/computer[COLOR="#FF0000"] mini@192.168.1.227:[/COLOR]/home/mini/Documents/ 

[LIST]
[*]The exclude needs something to match, not the full connection-rsync source string.
[*]I don't know what you think the -e option does.  It isn't needed and doesn't include a connection method, so it is wrong.
[*]Both sides of the SOURCE/DEST cannot be remote, if that was the intent. I cannot really tell.  I.e. they can't BOTH have IPs and logins.  If you want to copy files on the same machine, you don't need any IPs in the rsync part.

```
ssh mini@1.2.3.4  rsync -av   {SOURCE}    {TARGET}
```
[/LIST]

The manpage synopsis shows pretty clearly that only 1-side of the src or dest can be remote:
```
         Pull: rsync [OPTION...] [COLOR="#008000"][USER@]HOST:[/COLOR]SRC... [DEST]
         Push: rsync [OPTION...] SRC... [COLOR="#008000"][USER@]HOST:[/COLOR]DEST
```
Both the SRC and the DEST should be provided to prevent confusion.

Is there a reason you aren't using the sample commands I've posted?

---

