---
title: "what did I do?"
date: 2008-01-04
forum: General Help
---

### Post by thick0 on 2008-01-04
I don't know whether anyone can comment on this but here is my predicament. Running feisty with beryl (HP Compaq nx6120). I have been using this for a few months now.

Yesterday I was happily working away with 4 workspaces each with their own apps running. All beryl effects working.

Tonight I sign on, beryl is not there and I have only 2 workspaces. Did a "ps -e | grep beryl" and I can see beryl-manager. Went to system->preferences and enabled visual effects and that basically stuffed the system so I had to power down. :(

I did this a few times, couldn't find my missing workspaces and couldn't get beryl to start. I wanted to check the system but I typed the command wrongly "ps -e | beryl". This seemed to reload beryl, my missing workspaces re-appeared and all effects are working again. :)

What does ps -e | beryl do?

---

### Post by kpkeerthi on 2008-01-04
YOu just launched beryl and passed the output of **ps -e** to it, which ofcourse beryl would have ignored.

---

