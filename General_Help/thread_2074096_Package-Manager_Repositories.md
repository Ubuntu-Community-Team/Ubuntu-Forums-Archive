---
title: "Package-Manager Repositories"
date: 2012-10-20
forum: General Help
---

### Post by Yumi on 2012-10-20
Am on Quantal now. When I look at "Package Manager - Setting - Repositories - Other Software" there are still old entries as far back as natty but non for Quantal. Just a couple of lines "Disabled on update to Quantal". I am unable to remove those entries, the button is greyed out.

Looked at my "/etc/apt/sources.list" and all looks ok, everything set to Quantal.

Where does the Package-Manager find this old entries and how can I tidy things up?
Where can I find a list of current repositories for "Other Software"?

The problem behind me looking at the repositories is that I upgraded to Quantal during the final Beta-Version without problems. But now for 3 days I get the "Partial Update" message which I avoid. Not a real problem, I just wait, but it prompted me to have a look.

Michael

---

### Post by jerrrys on 2012-10-21
Look in /etc/apt/sources.list**.d**

---

### Post by Yumi on 2012-10-21
Thanks. Found a lot of old entries where you suggested and tidied up. Never dived further into the structure then sources.list before.

---

