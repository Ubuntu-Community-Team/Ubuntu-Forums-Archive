---
title: "Newest updates just broke Videos"
date: 2019-02-03
forum: General Help
---

### Post by fr33z0n3r on 2019-02-03
I updated a bunch of packages from the Software Updater today,  and it broke Videos.  I have Ubuntu 18.04.1 LTS.

The updates included Videos, as well as video related packages (mesa related) as well as kernel updates.

When I try to open Videos (directly - no file) it appears in the app bar on the left side of the screen for an instant and then disappears.  VLC is able to work normally.

If I run totem at the command line I get this:
```
: CommandLine Error: Option 'help-list' registered more than once!
LLVM ERROR: inconsistency in registered CommandLine options

```

Anyone have ideas on how I can troubleshoot or fix?  Given this occurred after an update,  I feel like its a bug.

Well, uninstalling the video driver amdgpu from AMD seems to have fixed this.

So the issue may lie with them.  I'm going to try reinstalling to see if this is persistent. 

I got the issue to go away after removing most non-ubuntu provided software.  But since reinstalling most of that,  the issue has not returned.  Now I will be installing steam.

I beleive that the issue was caused by some various driver incompatibilities.  I have purged all installed GPU drivers and am now using the OS drivers as well as these packages suggested by Valve :

[https://github.com/ValveSoftware/Proton/wiki/Requirements#amdintel](https://github.com/ValveSoftware/Proton/wiki/Requirements#amdintel)

---

