---
title: "How to deal with notice &quot;bash:sh/zsh: no such a directory&quot;"
date: 2015-06-01
forum: General Help
---

### Post by Yu_Lu on 2015-06-01
Hello everyone, 

Recently, I study via Udacity installing and configuring git tool on my ubuntu 14.04 LTS system. I meet a problem as I follow the instructions to set some prompt settings. What I did is to place two files "git-completion.bash" and "git-prompt.sh" that were from Udacity. Then, I, following the specifications of the note of the course, appended the content of the file "bash_prompt" to the file ".bashrc" locating in my home directory; the content is selected (highlighted) in the gedit.

Any helps or advice are deeply appreciated!
Thank you for browsing!
[ATTACH=CONFIG]262355[/ATTACH]

---

### Post by corti-nico on 2015-06-01
> **Yu_Lu said:**
> Hello everyone, 

Recently, I study via Udacity installing and configuring git tool on my ubuntu 14.04 LTS system. I meet a problem as I follow the instructions to set some prompt settings. What I did is to place two files "git-completion.bash" and "git-prompt.sh" that were from Udacity. Then, I, following the specifications of the note of the course, appended the content of the file "bash_prompt" to the file ".bashrc" locating in my home directory; the content is selected (highlighted) in the gedit.

Any helps or advice are deeply appreciated!
Thank you for browsing!
[ATTACH=CONFIG]262355[/ATTACH]

Can you please post here your "git-completion.bash" and "git-prompt.sh", you're probably loosing a #!/bin/bash on top ;)

---

### Post by Yu_Lu on 2015-06-03
The link of onedrive (Microsoft) to the file git-completion.bash:
[https://onedrive.live.com/redir?resid=e3e670d36117e6e1!3034&authkey=!ACL0yBdy_zTkSUw&ithint=file%2cbash](https://onedrive.live.com/redir?resid=e3e670d36117e6e1!3034&authkey=!ACL0yBdy_zTkSUw&ithint=file%2cbash)

The link to the file git-prompt.sh:
[https://onedrive.live.com/redir?resid=e3e670d36117e6e1!3033&authkey=!AGNaxj2VNxJTLBQ&ithint=file%2csh](https://onedrive.live.com/redir?resid=e3e670d36117e6e1!3033&authkey=!AGNaxj2VNxJTLBQ&ithint=file%2csh)

And, thank you.

---

### Post by sisco311 on 2015-06-03
The error message indicates that at some point your shell tries to run the `sh/zsh' command. I noticed that both files start with a comment:  `# bash/zsh ...' .  


Check your local copy of the files and make sure that you didn't miss to copy and paste a few characters from the beginning of one of them. ;)

---

### Post by Yu_Lu on 2015-06-03
Thank you for helping me. It turns out that I made a mistake of copying and pasting by ignoring selecting manually an appropriate encoding option for saving the file. The code is from a website, so I bet it may be displayed with another one encoding.

---

