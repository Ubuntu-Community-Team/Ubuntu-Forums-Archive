---
title: "[solved] shim packages are seen as obsolete"
date: 2018-09-25
forum: General Help
---

### Post by Qew on 2018-09-25
I did an update in Synaptic about a week or so ago, which updated two packages, shim (version 15+1533136590.3beb971-0ubuntu1) and shim-signed (version 1.37~18.04.1+15+1533136590.3beb971-0ubuntu1). All went well and I went on with my business. A few days later I was looking in Synaptic when I noticed I had two packages that were obsolete, which were shim and shim-signed. This was odd indeed. So, I went looking on the Net to see what's the issue, discovering that the packages had been shortly afterwards pulled, hence why they're now obsolete. The previous ones are now back in the repositories, but my versions on the packages are newer, so don't automatically get changed back.

Seeing that shim is involved with the EFI and booting, I'd rather not mess about with this like I would with other packages. So, what are my options here? Is it safe to remove these packages and install the original ones that are now the current? I tried to force the version down, but came up with complaints about doing so, so I didn't. Should I just wait till new shim packages that supersede the ones I now have, seeing that I'm not facing any issues with the running of Ubuntu or dual booting. I'm tending to the latter, but the OCD inside me looks at the "obsolete" as something that needs "fixing". I can live with it, but if it's easy to fix, then I'd rather do that.

Any ideas?

---

### Post by Qew on 2018-09-26
Bumping.

If this can't be answered here, any chance I can be directed where an answer is more likely? I've tried IRC, but got the same wall of silence.

Edit: I got an answer on IRC. The packages were indeed reverted. I was just unlucky when I updated. They'll shortly added back to Bionic from Bionic Proposed. I'll just wait till that happens.

---

### Post by #&amp;thj^% on 2018-09-26
> **Qew said:**
> Bumping.

If this can't be answered here, any chance I can be directed where an answer is more likely? I've tried IRC, but got the same wall of silence.

Edit: I got an answer on IRC. The packages were indeed reverted. I was just unlucky when I updated. They'll shortly added back to Bionic from Bionic Proposed. I'll just wait till that happens.
Your answer sounds better than mine.
Do you have Proposed enabled?
Also see this: [https://people.canonical.com/~ubuntu-archive/proposed-migration/bionic/update_excuses.html](https://people.canonical.com/~ubuntu-archive/proposed-migration/bionic/update_excuses.html)

It appears that this is related to upstream Debian.
> 
   shim-signed (1.34.9.2 to 1.37~18.04.1)

    Maintainer: Steve Langasek
    19 days old
    Not touching package due to block request by freeze (contact #ubuntu-release if update is needed)
    Depends: shim-signed shim (not considered)
    Not considered 



---

### Post by Qew on 2018-09-26
No, I don't have proposed selected.

The new packages were put up, then a change of mind happened or a correction of a mistake, and were reverted back to their original versions. I upgraded in the time that the packages were up, so now they're seen as not in the repository and seen as obsolete or self-installed.

I'll just wait till they return from proposed to bionic, which is apparently soon as the problem was fixed (grub 2 issue, apparently). I was more curious to sate my OCD seeing Obsolete in Synaptic when they shouldn't be there. Nothing's broken on my side.

Thanks. :)

---

