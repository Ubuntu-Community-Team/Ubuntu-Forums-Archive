---
title: "Manually installing an eye tracker for Linux"
date: 2008-06-17
forum: General Help
---

### Post by brr077 on 2008-06-17
Hi

I'm trying to set up cvEyeTracker ([http://thirtysixthspan.com/openEyes/software.html](http://thirtysixthspan.com/openEyes/software.html)) on the new Hardy edition of Ubuntu and I'm running into some trouble (I am new to compiling source in Linux)

cvEyeTracker calls for
OpenCV-0.9.5
libdc1394-0.9.4
libraw1394-0.10.1

I believe I've installed librawl correctly, but everything else seems to be giving me problems at one step or another. My technique is to use ubuntu's file extractor to put the source for each into its own folder and then cd to that folder, use "./configure" or "configure" (if it will let me, sometimes this does nothing) and then "make" followed by "make install". This worked for librawl but the others run into errors during make. I believe it's caused by my not adjusting the makefiles properly to account for my directories but I am in the dark about how to to do this correctly.

Could anyone here shine some light on this problem or perhaps give me a couple steps to go through to get cvEyeTracker on its feet? I'm very much enjoying the terminal but I wish I were a little more experienced.

thanks very much,

Ben

---

### Post by brr077 on 2008-06-18
Ok I used the package manager to get those three extensions but I'm still encountering errors when I run 'Make' in the cveyetracker folder:

eyetracker@eyetracker-desktop:~$ cd /home/eyetracker/Documents/retry/cvEyeTracker-1.2.5
eyetracker@eyetracker-desktop:~/Documents/retry/cvEyeTracker-1.2.5$ make
g++ -c -O2 cvEyeTracker.c -O2 -I/usr/local/include/opencv
In file included from cvEyeTracker.c:47:
remove_corneal_reflection.h:34:16: error: cv.h: No such file or directory
cvEyeTracker.c:58:21: error: highgui.h: No such file or directory
In file included from cvEyeTracker.c:47:
remove_corneal_reflection.h:42: error: variable or field ‘remove_corneal_reflection’ declared void
remove_corneal_reflection.h:42: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:42: error: ‘image’ was not declared in this scope
remove_corneal_reflection.h:42: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:42: error: ‘threshold_image’ was not declared in this scope
remove_corneal_reflection.h:42: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:42: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:42: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:43: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:43: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:43: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:43: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:45: error: variable or field ‘locate_corneal_reflection’ declared void
remove_corneal_reflection.h:45: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:45: error: ‘image’ was not declared in this scope
remove_corneal_reflection.h:45: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:45: error: ‘threshold_image’ was not declared in this scope
remove_corneal_reflection.h:45: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:45: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:45: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:46: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:46: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:46: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:46: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:48: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:48: error: ‘image’ was not declared in this scope
remove_corneal_reflection.h:48: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:48: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:48: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:48: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:49: error: expected primary-expression before ‘double’
remove_corneal_reflection.h:49: error: expected primary-expression before ‘double’
remove_corneal_reflection.h:49: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:49: error: initializer expression list treated as compound expression
remove_corneal_reflection.h:51: error: variable or field ‘interpolate_corneal_reflection’ declared void
remove_corneal_reflection.h:51: error: ‘IplImage’ was not declared in this scope
remove_corneal_reflection.h:51: error: ‘image’ was not declared in this scope
remove_corneal_reflection.h:51: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:51: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:51: error: expected primary-expression before ‘int’
remove_corneal_reflection.h:51: error: expected primary-expression before ‘double’
remove_corneal_reflection.h:52: error: expected primary-expression before ‘double’
remove_corneal_reflection.h:52: error: expected primary-expression before ‘int’
cvEyeTracker.c:99: error: expected constructor, destructor, or type conversion before ‘*’ token
cvEyeTracker.c:100: error: expected constructor, destructor, or type conversion before ‘*’ token
cvEyeTracker.c:101: error: expected constructor, destructor, or type conversion before ‘*’ token
cvEyeTracker.c:102: error: expected constructor, destructor, or type conversion before ‘*’ token
cvEyeTracker.c:103: error: expected constructor, destructor, or type conversion before ‘*’ token
cvEyeTracker.c:134: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:135: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:136: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:145: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:146: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:147: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:148: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:149: error: ‘CvPoint’ does not name a type
cvEyeTracker.c:283: error: ‘CvPoint’ does not name a type
cvEyeTracker.c: In function ‘int cal_calibration_homography()’:
cvEyeTracker.c:337: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:339: error: ‘vectors’ was not declared in this scope
cvEyeTracker.c: At global scope:
cvEyeTracker.c:476: error: ‘CvPoint’ does not name a type
cvEyeTracker.c: In function ‘int CalculateCalibration()’:
cvEyeTracker.c:593: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:597: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:601: error: ‘vectors’ was not declared in this scope
cvEyeTracker.c: At global scope:
cvEyeTracker.c:646: error: variable or field ‘Draw_Cross’ declared void
cvEyeTracker.c:646: error: ‘IplImage’ was not declared in this scope
cvEyeTracker.c:646: error: ‘image’ was not declared in this scope
cvEyeTracker.c:646: error: expected primary-expression before ‘int’
cvEyeTracker.c:646: error: expected primary-expression before ‘int’
cvEyeTracker.c:646: error: expected primary-expression before ‘int’
cvEyeTracker.c:646: error: expected primary-expression before ‘int’
cvEyeTracker.c:646: error: expected primary-expression before ‘double’
cvEyeTracker.c: In function ‘void Show_Calibration_Points()’:
cvEyeTracker.c:668: error: ‘scene_image’ was not declared in this scope
cvEyeTracker.c:668: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:668: error: ‘CV_RGB’ was not declared in this scope
cvEyeTracker.c:668: error: ‘Draw_Cross’ was not declared in this scope
cvEyeTracker.c: In function ‘void Zero_Calibration()’:
cvEyeTracker.c:676: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:679: error: ‘pucalipoints’ was not declared in this scope
cvEyeTracker.c:682: error: ‘crcalipoints’ was not declared in this scope
cvEyeTracker.c:685: error: ‘vectors’ was not declared in this scope
cvEyeTracker.c: In function ‘void Set_Calibration_Point(int, int)’:
cvEyeTracker.c:697: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:701: error: ‘pucalipoints’ was not declared in this scope
cvEyeTracker.c:701: error: ‘pupil’ was not declared in this scope
cvEyeTracker.c:705: error: ‘crcalipoints’ was not declared in this scope
cvEyeTracker.c:705: error: ‘corneal_reflection’ was not declared in this scope
cvEyeTracker.c:709: error: ‘vectors’ was not declared in this scope
cvEyeTracker.c:709: error: ‘diff_vector’ was not declared in this scope
cvEyeTracker.c: In function ‘void Set_Calibration_Point1(int, int)’:
cvEyeTracker.c:727: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:731: error: ‘pucalipoints’ was not declared in this scope
cvEyeTracker.c:731: error: ‘pupil’ was not declared in this scope
cvEyeTracker.c:739: error: ‘vectors’ was not declared in this scope
cvEyeTracker.c: In function ‘void Activate_Calibration()’:
cvEyeTracker.c:769: error: ‘scenecalipoints’ was not declared in this scope
cvEyeTracker.c:775: error: ‘pucalipoints’ was not declared in this scope
cvEyeTracker.c:781: error: ‘crcalipoints’ was not declared in this scope
cvEyeTracker.c: In function ‘void on_mouse_scene(int, int, int, int)’:
cvEyeTracker.c:797: error: ‘CV_EVENT_LBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c:802: error: ‘CV_EVENT_MBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c:807: error: ‘CV_EVENT_RBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c: In function ‘void on_mouse_eye(int, int, int, int)’:
cvEyeTracker.c:819: error: ‘CV_EVENT_LBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c:821: error: ‘pupil’ was not declared in this scope
cvEyeTracker.c:832: error: ‘CV_EVENT_MBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c:836: error: ‘CV_EVENT_RBUTTONDOWN’ was not declared in this scope
cvEyeTracker.c: At global scope:
cvEyeTracker.c:855: error: variable or field ‘Normalize_Line_Histogram’ declared void
cvEyeTracker.c:855: error: ‘IplImage’ was not declared in this scope
cvEyeTracker.c:855: error: ‘in_image’ was not declared in this scope
make: *** [cvEyeTracker.o] Error 1

Is there an obvious solution to this that I'm too young to see?

---

### Post by angustia on 2008-09-09
it is looking for the file "cv.h" in /usr/local/include/opencv

did you install compiling from source or from package?


i can compile it with libcv-dev, libcvaux-dev, libraw1394-dev andlibdc1394-13-dev from synaptic, but i had to change some of the source code because it was written for an old version of libcv (opencv).

---

