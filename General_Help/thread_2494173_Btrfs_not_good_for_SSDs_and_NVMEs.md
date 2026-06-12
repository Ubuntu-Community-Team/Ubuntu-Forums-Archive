---
title: "Btrfs not good for SSDs and NVMEs?"
date: 2024-01-07
forum: General Help
---

### Post by Advait on 2024-01-07
I'm a basic home computer user. No programming, no servers, no video editing, no gaming. Only browsing and a few other simple apps. No home network or NAS. Just my laptop and 2 sim card wifi hotspots. No stand alone hardware router.

I'm running 22.04 and ext4 in an AMD laptop with 2 internal nvmes. I've been thinking of switching to Btrfs cuz snapshots look like a great capability to have. But I just browsed some posts that warn that Btrfs can quickly wear out SSDs and nvmes.

[https://unix.stackexchange.com/questions/748009/how-to-measure-the-role-of-btrfs-in-ssd-wear-on-my-pc](https://unix.stackexchange.com/questions/748009/how-to-measure-the-role-of-btrfs-in-ssd-wear-on-my-pc)

Should I stay away from Btrfs because it can quickly wear out my nvmes?

Are there some technical tricks that can prevent Btrfs from quickly wearing out my nvmes?

I browsed this post [https://unix.stackexchange.com/questions/748009/how-to-measure-the-role-of-btrfs-in-ssd-wear-on-my-pc](https://unix.stackexchange.com/questions/748009/how-to-measure-the-role-of-btrfs-in-ssd-wear-on-my-pc) but it was above my newbie head. And no one replied to it.

Update: I did some more googling and searching and found a few posts and threads that said current Btrfs with recent kernels = no problem with wearing out nvmes. I'll take that as my solution.

They pointed out that Btrfs was default on OpenSuse and Fedora and they wouldn't use Btrfs if it caused that kind of problem.

---

