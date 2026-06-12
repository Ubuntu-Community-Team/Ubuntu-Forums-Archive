---
title: "Can't get correct JAVA_PATH after removing Oracle Java 7"
date: 2013-10-10
forum: General Help
---

### Post by Peter_Brandon on 2013-10-10
I installed and then removed Oracle Java 7, but the PATH and JAVA_HOME environment variables still point to /usr/lib/jvm/java-7-oracle.  When I look in update-alternatives, either for java or javac, these correctly point to java-6-openjdk-amd64.  What I'm finding challenging is figuring out where PATH and JAVA_HOME are being set to java-7.  I've looked in:  ~/.profile**, **~/.bashrc, /etc/environment, /etc/profile, /etc/bash.bashrc.  

I guess I could 'solve' the problem by, say, changing /etc/environment, but that likely won't erase java-7 from the PATH and will correctly set JAVA_HOME only if the environment file is the last one run.  It would be best to find out what is setting the paths to java-7 and remove that.

I have tried manually resetting to java-6 and then running jEdit.  This works if I run jEdit from the command line, but for some reason the menu commands no longer work.

Your thoughts would be appreciated!

---

### Post by Peter_Brandon on 2013-10-12
bump.

I think I've looked everywhere that JAVA_HOME could be getting set and yet, somehow, it's being set to a value that is stopping all my java-based programs from functioning.  Does anyone have any ideas how this could be happening?

---

