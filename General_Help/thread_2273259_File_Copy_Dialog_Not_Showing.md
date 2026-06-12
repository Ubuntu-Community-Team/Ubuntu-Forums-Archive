---
title: "File Copy Dialog Not Showing?"
date: 2015-04-11
forum: General Help
---

### Post by avielmenter on 2015-04-11
I've seen other people with this issue, but none of their solutions have worked for me. I'm copying a few hundred megabytes of files to a server via FTP, but once I tell the files to merge / replace, no progress bar dialog appears. On the sidebar, there's a small progress bar over the File Browser icon, but this doesn't give me much information.

When I right-click the file browser icon and click "show copy dialog", nothing happens, except when I alt tab to the file browser, it doesn't do anything, suggesting it's creating an invisible window.

When I list windows in wmctrl, it tells me that "File Operations" is a window, but when I do wmctrl -R "File Operations", nothing happens. If I've closed down the file operations window, then open it via wmctrl, the File Browser icon in the sidebar wiggles, but nothing displays.

Never does a file copy dialog window (invisible or otherwise) appear when I am alt-tabbing.

How can I see the file copy dialog?

---

