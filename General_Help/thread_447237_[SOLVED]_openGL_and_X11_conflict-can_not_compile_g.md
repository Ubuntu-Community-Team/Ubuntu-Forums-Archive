---
title: "[SOLVED] openGL and X11 conflict-can not compile gui part of the program"
date: 2007-05-17
forum: General Help
---

### Post by bobbyubun on 2007-05-17
Hi Forum members,

I am compiling SUMO program([http://sumo.sourceforge.net/index.shtml](http://sumo.sourceforge.net/index.shtml)) that is a traffic simulator. It consists of several programs and a graphic simulator(sumo-guisim).I successfuly run configure but when i run make command (compile) I get the error as follows in the terminal that i run the make:

[I]92: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:293: undefined reference to `glMatrixMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:294: undefined reference to `glLoadIdentity'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:295: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:296: undefined reference to `glScaled'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:297: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:299: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:315: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:317: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:318: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:321: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:323: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:325: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:326: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:331: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:332: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:333: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:334: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:338: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:339: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:340: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:341: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:342: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:399: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:400: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:401: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:395: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:396: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:390: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:391: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:392: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:393: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:394: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:381: undefined reference to `glColor3f'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:382: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:385: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:422: undefined reference to `glColor3d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:445: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:447: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:449: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:450: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:452: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:453: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:454: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:455: undefined reference to `glEnd'
./utils/gui/tracker/libguiutilstracker.a(GUITLLogicPhasesTrackerWindow .o): In function `GUITLLogicPhasesTrackerWindow::GUITLLogicPhasesTr ackerPanel:nPaint(FX::FXObject*, unsigned int, void*)':
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:613: undefined reference to `glViewport'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:614: undefined reference to `glClearColor'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:615: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:616: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:617: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:618: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:619: undefined reference to `glEnable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:620: undefined reference to `glDisable'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:621: undefined reference to `glLineWidth'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:622: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:624: undefined reference to `glClear'
/home/bobby/sumo-0.9.5/src/utils/gui/tracker/GUITLLogicPhasesTrackerWindow.cpp:626: undefined reference to `glFlush'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:149: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:150: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:152: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:153: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:154: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:155: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:156: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:157: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:158: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:159: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:160: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:161: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:162: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:128: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:129: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:130: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:131: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:132: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:133: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:134: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:135: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:136: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:137: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:138: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:139: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:140: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:269: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:270: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:271: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:272: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:273: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:274: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:275: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:254: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:255: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:256: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:257: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:258: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:259: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:260: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawTriangleAtEnd(Line2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:378: undefined reference to `glPushMatrix'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:379: undefined reference to `glTranslated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:380: undefined reference to `glRotated'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:381: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:382: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:383: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:384: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:385: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:386: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:109: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:110: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:114: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:118: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:338: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:344: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:345: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:346: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:347: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:349: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:350: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:351: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:352: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:357: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:358: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:359: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:360: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:362: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:363: undefined reference to `glVertex2d'
./utils/glutils/libglutils.a(GLHelper.o):/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:364: more undefined references to `glVertex2d' follow
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawOutlineCircle(float, float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:365: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledCircle(float, int, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:298: undefined reference to `glPolygonMode'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:304: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:305: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:306: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:307: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:308: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:313: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:314: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:315: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:316: undefined reference to `glVertex2d'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:317: undefined reference to `glEnd'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:163: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawBoxLine(Position2D const&, float, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:141: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:276: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawLine(Position2D const&, float, float)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:261: undefined reference to `glPopMatrix'
./utils/glutils/libglutils.a(GLHelper.o): In function `GLHelper::drawFilledPoly(Position2DVector const&, bool)':
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
/home/bobby/sumo-0.9.5/src/utils/glutils/GLHelper.cpp:120: undefined reference to `glEnd'
./utils/glutils/libglutils.a(polyfonts.o): In function `drawWideChar':
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1004: undefined reference to `glBegin'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1022: undefined reference to `glVertex2f'
/home/bobby/sumo-0.9.5/src/utils/glutils/polyfonts.c:1024: undefined reference to `glEnd'
collect2: ld returned 1 exit status
make[3]: *** [sumo-guisim] Error 1
make[3]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/bobby/sumo-0.9.5/src'
make: *** [all-recursive] Error 1

[/I]
I have already run:

sudo apt-get install libgl1-mesa-dev
sudo apt-get install libglu1-mesa-dev
sudo apt-get install mesa-common-dev

and xlibmesa-glu, libx11-dev, libgludev, libsdldev

But I guess i did not install the correct library yet OR i have link problem Or It might be some conflict between X11 and gl

I am still puzzled with these errors since the OpenGL libraries are in /usr/lib

I appreciate help or any hint
thanks-bobby

---

