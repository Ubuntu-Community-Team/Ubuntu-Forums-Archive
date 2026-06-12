---
title: "Java Visual Glitch"
date: 2008-05-07
forum: General Help
---

### Post by Mizutsuki on 2008-05-07
When I upgraded to hardy I introduced a strange set of visual glitches.  I'm running hardy on a 64 bit system, the glitch occurs regardless of version of the jvm (1.5/1.6-x86/amd64) and is not affected by the compiz settings.  I have this problem at work, but not at home, where I'm running the x86 version (I'm not sure the architecture is to blame, though.)  The problem usually occurs when text is modified on the screen, but sometimes occurs when a frame is first started or on the menus at the top of the frame.  Occasionally this bug can be debilitating when the artifacts start appearing everywhere I can't read the text on the screen, but most of the time it's just mildly annoying.  Attached are pictures of the bug.  Any ideas?

---

### Post by Mizutsuki on 2008-05-12
Two things:
1. *bump*
2. I wanted to be more explicit, so here's a very simple test case (Java app, it's just a text-area):
```
import java.awt.Container;

import javax.swing.JFrame;
import javax.swing.JTextArea;

public class Test {
  public static void main(String args[]) {
    JFrame frame = new JFrame("Test");
    Container content = frame.getContentPane();

    JTextArea leftTextArea = new JTextArea();
    content.add(leftTextArea);

    frame.setSize(150, 150);
    frame.setVisible(true);
  }
}
```
Just pop that in and execute it, then type in (manually) the following:
"asdf
asdf
asdf
asdf
asdf"
and if the shape of the characters gets distorted, then you have the same problem.  I'd love to hear if anyone else is having this problem.
Thanks,
Stephen

---

### Post by Mizutsuki on 2008-05-13
FYI, I've added a bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+bug/230048](https://bugs.launchpad.net/ubuntu/+bug/230048)

---

### Post by Mizutsuki on 2008-05-19
I really need this fixed, and no one is responding to the bug report, I just wanted to ask if maybe I filled it out wrong?  I tried going through and searching from it from the launchpad main page and I couldn't find it, which leads me to believe that no developer is going to come upon it and fix it, so is there anything I can do to increase the likelihood of it getting noticed?
Thanks

---

