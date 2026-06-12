---
title: "All items from /var/run are showing up in Nautilus' trash folder"
date: 2007-05-04
forum: General Help
---

### Post by cdmarcus on 2007-05-04
I just went to empty my trash, when I noticed that all the items from /var/run/ were showing up in the trash. I checked ~/.Trash, and there was nothing there. Same with /root/.Trash. The items weren't copies of items from /var/run/ because when I went to their properties window, it said, "Location: /var/run/"

Can anyone tell me why Nautilus would be displaying these items in the trash?

---

### Post by dcstar on 2007-05-05
> **cdmarcus said:**
> I just went to empty my trash, when I noticed that all the items from /var/run/ were showing up in the trash. I checked ~/.Trash, and there was nothing there. Same with /root/.Trash. The items weren't copies of items from /var/run/ because when I went to their properties window, it said, "Location: /var/run/"

Can anyone tell me why Nautilus would be displaying these items in the trash?

The /var/run files seem to be created on boot, and I suspect that they may be "refreshed" after a certain period.

Does your machine stay on all the time?

---

### Post by cdmarcus on 2007-05-05
> **dcstar said:**
> The /var/run files seem to be created on boot, and I suspect that they may be "refreshed" after a certain period.

Does your machine stay on all the time?

No, it's a laptop. The problem here isn't that /var/run exists, the problem is that for some reason, the trash is showing any items in /var/run as trash items.

---

### Post by rei_t_ex on 2007-05-13
I have recently started having the same problem (after either updating or uninstalling something via Synaptic Package Manger, I believe).

The .Trash folder is always empty, but the entire contents of /var/run show up in Nautilus's "trash:".

If no one has managed to solve this, does anyone at least know how Nautilus handles this "trash:"?  Apparently it does more than simply looking in the .Trash folder...

Any help would be deeply appreciated.

---

