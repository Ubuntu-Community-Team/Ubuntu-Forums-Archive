---
title: "Help with getting XGL or AIGLX woking with integrated savage video card"
date: 2007-02-13
forum: General Help
---

### Post by nolageek on 2007-02-13
I've been trying for a few days now to get either Beryl or Compiz working under Edgy.  I tried the How-To at Beryl to get XGL working and when I run startxgl.sh my screen turns black and I get weird purple icons and super-pixelated mouse trails.  Although I see lots of info on ATI and nVidea and Intel... where would savage apply?  I saw somewhere that savage is 'sort of' supported under AIGLX, but it doesn't say which to use... ATI or nVidea.

Here is the video driver line from lspci
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Vincent

---

### Post by nolageek on 2007-02-14
bump

---

### Post by dcstar on 2007-02-14
> **nolageek said:**
> I've been trying for a few days now to get either Beryl or Compiz working under Edgy.  I tried the How-To at Beryl to get XGL working and when I run startxgl.sh my screen turns black and I get weird purple icons and super-pixelated mouse trails.  Although I see lots of info on ATI and nVidea and Intel... where would savage apply?  I saw somewhere that savage is 'sort of' supported under AIGLX, but it doesn't say which to use... ATI or nVidea.

Here is the video driver line from lspci
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

Vincent

A S3 card is a S3 card - not ATI or Nvidia.

You should already be using the S3 driver in your xorg.conf file, but I'm not sure there is Direct Rendering support for these cards.

I have a S3 Unichrome integrated video on my PC, but I went out and purchased an old Nvidia AGP video card because it has better support under Ubuntu (and it works far better that my other one, anyway!).

Best $10 I have spent on hardware in a while.........

---

