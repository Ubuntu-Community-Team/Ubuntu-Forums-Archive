---
title: "Boot Repair"
date: 2020-05-05
forum: General Help
---

### Post by mediafire2 on 2020-05-05
Hello, how can I restore booting to my Ubuntu installation, I always get stuck at black screen with mouse pointer only shortly before login screen (desktop settings are already loaded):

[ATTACH=CONFIG]285753[/ATTACH]

I've tried installing and running Boot-Repair to live session from installation CD, which resulted to successful repair and reboot, but the problem persists. Any other options?

---

### Post by CelticWarrior on 2020-05-05
There's really no point in posting a huge image of a black screen. Saying so is enough. Posting relevant information about the Ubuntu release/version and hardware specifications is what you should have done instead.
**And Boot Repair is NOT for such cases.**

Here's what can be considered a generic guide for troubleshooting: [https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by slickymaster on 2020-05-05
@mediafire2:

Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by oldfred on 2020-05-05
Boot-Repair is for fixing boot issues, mostly grub related.
But black screen is normally after you have booted thru grub, but then have video issues so system does not complete boot.
Can you boot to grub menu? If only one system, Escape key after UEFI screen but before grub normally appears. Or if BIOS then hold shift key.
Then use recovery mode to boot to command line/terminal.

What video card/chip?

---

### Post by VMC on 2020-05-05
Can you log in to another virt terminal; Ctrl+Alt+F?. See if it responds.

---

