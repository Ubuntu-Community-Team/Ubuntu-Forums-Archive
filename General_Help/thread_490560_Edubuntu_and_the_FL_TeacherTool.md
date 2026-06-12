---
title: "Edubuntu and the FL_TeacherTool"
date: 2007-07-02
forum: General Help
---

### Post by yochaigal on 2007-07-02
I've got a working LTSP test lab at my office. I can get x11vnc running just find, thus enabling me to see "over" the network what a thin client is looking at.

However I can't get the FL_Teacher tool to work! I keep getting this error message when compiling:

server@edubuntu:~/Desktop/Fl_TeacherTool-0.34$ make
g++ -Wall `fltk-config --cxxflags` -D HOSTINFOFILE=\"/usr/local/etc/fl_teachertool/HOST_INFO_FILE\" -D VNCREFLECTOR=\"/usr/bin/vncreflector\" -D TIGHTVNCVIEWER=\"/usr/bin/teachertool-vncviewer\" -D REALVNCVIEWER=\"/usr/bin/vncviewer\" -D FLTTMESSAGE=\"/usr/local/bin/fl_TTmessage\" -D BINDIR=\"/usr/local/bin\" -D SBINDIR=\"/usr/local/sbin\"  -c Fl_TeacherTool.cxx
Fl_TeacherTool.cxx:49:21: error: X11/xpm.h: No such file or directory
Fl_TeacherTool.cxx: In function ‘int main(int, char**)’:
Fl_TeacherTool.cxx:297: error: ‘XpmCreatePixmapFromData’ was not declared in this scope
make: *** [Fl_TeacherTool.o] Error 1
server@edubuntu:~/Desktop/Fl_TeacherTool-0.34$ 

I have installed all the necessary dependencies, and I can't find any info on the error code.  I've been utilizing this guide:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPFl_TeacherTool](https://help.ubuntu.com/community/UbuntuLTSP/LTSPFl_TeacherTool)
thanks!

---

### Post by yochaigal on 2007-07-02
figured it out. I need the xpm-dev package found in synaptic.

thanks

---

