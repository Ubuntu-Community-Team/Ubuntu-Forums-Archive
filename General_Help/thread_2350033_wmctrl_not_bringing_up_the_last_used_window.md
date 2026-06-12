---
title: "wmctrl not bringing up the last used window"
date: 2017-01-20
forum: General Help
---

### Post by Salil_Surendran on 2017-01-20
I have a script as such "wmctrl -x -a "$1"" that brings up the window passed as the argument to the script for eg. wmctrl -x -a "Firefox" activates firefox. However, with applications that have multiple windows it doesn't bring up the last used windows. Consider I have 3 windows open in LibreOffice Writer named 'Doc 1', 'Doc 2' and 'Doc 3' and I am on Doc 3 and I move to another application. Executing the script brings up 'Doc 1' and not 'Doc 3' which was last used. Any flag to fix this problem in wmctrl?

---

