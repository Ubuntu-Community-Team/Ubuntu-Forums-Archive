---
title: "Can't erase a dvd+rw"
date: 2007-05-05
forum: General Help
---

### Post by adamthompson on 2007-05-05
When I try to erase a dvd+rw using "dvd+rw-format -blank /dev/dvd", I get this error message:

* DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

Does anyone have any idea what the problem is? I'm using Edgy. Thanks.

---

### Post by dcstar on 2007-05-05
> **adamthompson said:**
> When I try to erase a dvd+rw using "dvd+rw-format -blank /dev/dvd", I get this error message:

* DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 6.1.
* 4.7GB DVD+RW media detected.
- illegal command-line option for this media.
- **you have the option to re-run dvd+rw-format with:**
  **-lead-out**  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  **-force**     to enforce new format (not recommended)
             and wipe the data.

Does anyone have any idea what the problem is? I'm using Edgy. Thanks.

Well, it is saying that you shouldn't reformat unless you use those options.

---

