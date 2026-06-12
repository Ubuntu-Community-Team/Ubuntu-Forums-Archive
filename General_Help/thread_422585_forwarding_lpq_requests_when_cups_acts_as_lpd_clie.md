---
title: "forwarding lpq requests when cups acts as lpd client"
date: 2007-04-25
forum: General Help
---

### Post by supermihi on 2007-04-25
I am using feisty fawn on a computer that prints through an LPD printer server. So far I used lprng on that computer, so it just acted as an LPD client. I could print via lpr, view the queue with lpq and so on.
But now I'd like to use cups, since I know and like it more than LPRng. I added every printer on the lpd server in cups and can print jobs with lpr like always before. But now if I query the printers with lpq, I always get "printer ready. No entries", since the local cups server already has sended the job to the server - but I can't examine at which position in the queue my job is at the server.
Is there a way to "forward" the lpq request to the server, actually showing the same information as if I'd use lpq from LPRng acting as simple LPD client?

regards
Michael

---

