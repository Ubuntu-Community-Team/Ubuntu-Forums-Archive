---
title: "VLC / SMPlayer - YouTube Problems"
date: 2021-11-13
forum: General Help
---

### Post by Shibblet on 2021-11-13
Has anyone noticed lately, that if you paste a YouTube URL into VLC or SMPlayer, that it has a really hard time keeping up with the data?

Buffer after buffer, it's like the data doesn't stream in fast enough.

Play it in a browser, and there are no issues what-so-ever...

Is it just me, or are others having this issue?

---

### Post by DuckHook on 2021-11-13
YouTube is constantly monkeying around with their algorithms trying to break the third party download collective. Here is an earlier thread dealing with the same issue: [https://ubuntuforums.org/showthread.php?t=2467978](https://ubuntuforums.org/showthread.php?t=2467978)

The latest YouTube gambit is to throttle download speeds to only what would reasonably be expected from interactive streaming and to treat any faster download as illegal and therefore subject to throttling so severe that it renders the resulting stream basically unusable. Essentially, the stream is constructed so that it recognizes browsers as legal interactive devices, but apps like VLC and SMPlayer as illegal non-interactive ones.

Actually, there's nothing wrong with VLC et al. It's just that YouTube wants to foist their advertising and tracking onto all viewers, and they can't do that if you bypass the browser. With minimal effort, it is easy to disable tracking and advertising within a browser too, but most people don't, so YouTube has chosen this clumsy and brutish half-measure to keep the uninformed chained to their tracking shackles.

It's just another silly skirmish in the ongoing war between YouTube and downloaders who value their privacy. Powerusers (especially Linux powerusers) have already largely bypassed this latest YouTube ploy but, as per linked thread above, this forum does not permit discussion of what those bypasses are. Please don't delve further into such bypasses or staff will be forced to close the thread.

The upshot is that, since VLC and SMPlayer rely on older algorithms/dependencies to play YouTube, such apps have effectively been nerfed. Until these apps are updated to use the newer algorithms, they can't be used for YouTube. To my knowledge, there's no ETA on such updates.

---

### Post by Shibblet on 2021-11-13
> **DuckHook said:**
> YouTube is constantly monkeying around with their algorithms trying to break the third party download collective. Here is an earlier thread dealing with the same issue: [https://ubuntuforums.org/showthread.php?t=2467978](https://ubuntuforums.org/showthread.php?t=2467978)

The latest YouTube gambit is to throttle download speeds to only what would reasonably be expected from interactive streaming and to treat any faster download as illegal and therefore subject to throttling so severe that it renders the resulting stream basically unusable. Essentially, the stream is constructed so that it recognizes browsers as legal interactive devices, but apps like VLC and SMPlayer as illegal non-interactive ones.

Actually, there's nothing wrong with VLC et al. It's just that YouTube wants to foist their advertising and tracking onto all viewers, and they can't do that if you bypass the browser. With minimal effort, it is easy to disable tracking and advertising within a browser too, but most people don't, so YouTube has chosen this clumsy and brutish half-measure to keep the uninformed chained to their tracking shackles.

It's just another silly skirmish in the ongoing war between YouTube and downloaders who value their privacy. Powerusers (especially Linux powerusers) have already largely bypassed this latest YouTube ploy but, as per linked thread above, this forum does not permit discussion of what those bypasses are. Please don't delve further into such bypasses or staff will be forced to close the thread.

The upshot is that, since VLC and SMPlayer rely on older algorithms/dependencies to play YouTube, such apps have effectively been nerfed. Until these apps are updated to use the newer algorithms, they can't be used for YouTube. To my knowledge, there's no ETA on such updates.

Ugh... thank you for the information.  This stops me from trying to figure out the problem.  I guess I just deal for now.

---

### Post by DuckHook on 2021-11-17
FWIW, SMPlayer is also available as a snap. The latest snap will always be more current than the feature&#8209;frozen app that is in the repos.

---

