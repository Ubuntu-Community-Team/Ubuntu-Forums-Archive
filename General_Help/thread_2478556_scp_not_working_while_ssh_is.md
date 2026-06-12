---
title: "scp not working while ssh is"
date: 2022-08-29
forum: General Help
---

### Post by jakebriggs on 2022-08-29
Hi All

I'm having an issue scping from an ubuntu machine to a debian machine, and I was wondering if anyone could shed some light on the issue.

This has been an issue for a while across releases, but I am currently running Ubuntu 22.04 with openssh 1:8.9p1-3 from the repos on the machine I want to scp from and openssh 1:9.0p1-1+b1 on the target server.

Has anyone encountered this issue before? Will I need to manually install a newer version of openssh locally?

Here is the log on my client ubuntu machine
[https://pastebin.com/VQFFqSVq](https://pastebin.com/VQFFqSVq)

Here is the log on the server 
[https://pastebin.com/CrKrujBu](https://pastebin.com/CrKrujBu)

I did note that the old scp protocol is disabled by default in openssh 9.0, am I able to turn that back on?

I tried it with sftp, its replacement, and I have the exact same problem 

Here is the log on my client ubuntu machine
[https://pastebin.com/thGhWXCS](https://pastebin.com/thGhWXCS)

Here is the log on the server 
[https://pastebin.com/TE98Tpi6](https://pastebin.com/TE98Tpi6)


Jake

---

### Post by HermanAB on 2022-08-30
What is the command that you used?

It looks like you only checked whether a file is present and did not actually give a destination for it to be copied to.

---

### Post by jakebriggs on 2022-09-06
Right so I worked out what this was, after setting up a debian vm locally and trying to scp from there and the same problem happened - ruling out version differences. I also noticed rsync was failing so this was not an issue with ssh.

I had a faulty login script. After comparing the default login scripts on the aforementioned VM, I found that somehow /etc/bash.bashrc had an extra line on the non-working computer which was causing the login shell interactivity check to fail and was logging in scp interactively. I was for some reason executing ~/.bashrc in /etc/bash.bashrc and its interactivity check failed to return properly since you can only "return" from a function or sourced script and it was the error message (/home/jake/.bashrc: line 8: return: can only `return' from a function or sourced script) that was causing non-interactive sessions (like scp or rsync) to fail.

So, yeah a pebkac error I think lol, I must have put that there at some stage in the distant past.

---

