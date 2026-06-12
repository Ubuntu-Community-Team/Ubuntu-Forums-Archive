---
title: "QT applications all hang"
date: 2016-02-17
forum: General Help
---

### Post by ObsequiousNewt on 2016-02-17
Recently upon restarting my computer, I encountered a strange problem: no application dependent on QT will function. Instead, they start a process, but the process fails to do anything, or in fact print any output, and can only be manually killed (it will not close itself after any amount of time.)

At least one application (frescobaldi), which runs under Python, will print out the following error message when killed:
```
zeb@geonia:~$ frescobaldi 
^CQt: Session management error: IO error occured opening connection
Traceback (most recent call last):
  File "/usr/bin/frescobaldi", line 3, in <module>
    import frescobaldi_app.main
  File "/usr/lib/python2.7/dist-packages/frescobaldi_app/main.py", line 39, in <module>
    import app              # Construct QApplication
  File "/usr/lib/python2.7/dist-packages/frescobaldi_app/app.py", line 34, in <module>
    qApp = QApplication([os.path.abspath(sys.argv[0])] + sys.argv[1:])
KeyboardInterrupt
zeb@geonia:~$ uname -a
Linux geonia 3.19.0-49-generic #55~14.04.1-Ubuntu SMP Fri Jan 22 11:23:34 UTC 2016 i686 athlon i686 GNU/Linux
zeb@geonia:~$
```

I have been unable to locate any information regarding this problem. I have supplied the output of uname -a above. All of my packages are up to date.

Does anyone know how I may solve my problem, or at least print out any sort of useful error message?

EDIT: I forgot to mention an important detail: any programs that were started due to having been running when I restarted remain running, but I cannot start any new instances thereof.

---

### Post by ObsequiousNewt on 2016-03-02
I was able to fix the problem by removing (or renaming) the file ~/.kde/share/config/ksmserverrc. Unfortunately, this also removes all session data. Presumably there is an offending line in the file which may be changed, but I have not tested yet.

---

### Post by ObsequiousNewt on 2016-03-26
I have managed to isolate the trigger to a certain program. If Frescobaldi (a QT application for creating music scores with Lilypond) is in the previous session, then this problem will be triggered.

Oddly, however, simply starting Frescobaldi does not prevent usage of QT applications; it has to have been automatically started due to having been running at the close of the previous session.

It is possible that other applications similarly trigger this problem.

---

