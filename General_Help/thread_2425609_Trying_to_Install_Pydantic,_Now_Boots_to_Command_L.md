---
title: "Trying to Install Pydantic, Now Boots to Command Line"
date: 2019-08-27
forum: General Help
---

### Post by teddybouch on 2019-08-27
I'm running Ubuntu 18.04.3 LTS on an ASUS ROG laptop, and this afternoon I was trying to get pipenv and ultimately pydantic installed for a project I'm working on. I was having some trouble and realized that I had two versions of Python installed and thought that might be my issue, so I purged python2.6 and python 3.7 and somehow in the process I think I ended up with python3.6. Whatever the case was, pip still wasn't recognized as a valid command and it wasn't finding some other things, so I thought that maybe I should just restart the computer, let the environment refresh, and see what that did.

Well, now my computer only boots to the command line. I found other posts with this problem, but it seems to happen after upgrades to a new version of Ubuntu, which is not my situation, and in those other cases running 'startx' would get to the GUI, which also doesn't work for me. Running 'startx' seems to try to run the X server, then I get an error:

xf86EnableIOPorts: failed to set IOPL for I/o (Operation not permitted)
resize called 1920 1080
xinit: connection to X server lost

I'm thinking about trying to reinstall just the Ubuntu partition, but I'd rather not if I don't have to. Any suggestions?

---

