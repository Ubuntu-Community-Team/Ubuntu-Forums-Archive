---
title: "Compiling KPilot - help"
date: 2007-04-10
forum: General Help
---

### Post by peter_brewer on 2007-04-10
Hi.  I am not sure if this is the right place to post this.  I am trying to compile KPIlot as I want to be able to sync the extended pims.  I have compiled pilot-link and run the cmake scripts but get this set of errors at the end.  Does anyone know how I can resolve this.  I have little experience compiling on Linux.

make[3]: Entering directory `/home/pjb/kpilot/build-Linux2_6_20_14_generic'
[ 76%] Building CXX object conduits/knotes/CMakeFiles/conduit_knotes.dir/knotes-action.o
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:38:35: error: libkcal/calendarlocal.h: No such file or directory
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:147: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:147: error: ISO C++ forbids declaration of ‘CalendarLocal’ with no type
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:147: error: expected ‘;’ before ‘*’ token
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:149: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:149: error: ISO C++ forbids declaration of ‘List’ with no type
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:149: error: expected ‘;’ before ‘fNotes’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:154: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:154: error: ISO C++ forbids declaration of ‘ConstIterator’ with no type
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:154: error: expected ‘;’ before ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In constructor ‘KNotesAction::KNotesActionPrivate::KNotesActionPrivate()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:124: error: class ‘KNotesAction::KNotesActionPrivate’ does not have any field named ‘fNotesResource’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In destructor ‘KNotesAction::KNotesActionPrivate::~KNotesActionPrivate()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:137: error: ‘fNotesResource’ was not declared in this scope
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:139: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In member function ‘bool KNotesAction::openKNotesResource()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:262: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotesResource’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:262: error: expected type-specifier before ‘KCal’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:262: error: expected `;' before ‘KCal’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:265: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotesResource’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:267: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotes’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:267: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotesResource’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In member function ‘void KNotesAction::resetIndexes()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:283: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:283: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotes’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In member function ‘void KNotesAction::listNotes()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:290: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:290: error: expected `;' before ‘notes’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:291: error: ‘notes’ was not declared in this scope
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:294: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:294: error: expected `;' before ‘it’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:296: error: ‘it’ was not declared in this scope
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In member function ‘bool KNotesAction::addNewNoteToPilot()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:551: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:551: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fNotes’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:556: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:556: error: ‘j’ was not declared in this scope
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:556: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:563: warning: unused variable ‘newid’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:577: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: At global scope:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:690: warning: unused parameter ‘m’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:690: warning: unused parameter ‘memo’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:705: warning: unused parameter ‘memo’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc: In member function ‘int KNotesAction::addNoteToPilot()’:
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:723: error: ‘KCal’ has not been declared
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:723: error: ‘j’ was not declared in this scope
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:723: error: ‘class KNotesAction::KNotesActionPrivate’ has no member named ‘fIndex’
/home/pjb/kpilot/conduits/knotes/knotes-action.cc:750: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
make[3]: *** [conduits/knotes/CMakeFiles/conduit_knotes.dir/knotes-action.o] Error 1
make[3]: Leaving directory `/home/pjb/kpilot/build-Linux2_6_20_14_generic'
make[2]: *** [conduits/knotes/CMakeFiles/conduit_knotes.dir/all] Error 2
make[2]: Leaving directory `/home/pjb/kpilot/build-Linux2_6_20_14_generic'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/pjb/kpilot/build-Linux2_6_20_14_generic'
make: *** [all] Error 2

Up until the beginning of the errors it is successful with only a few warnings about virtual functions and non virtual destructors.

Thankyou for any help you can offer.

---

### Post by WW on 2007-04-10
The first error is
```

/home/pjb/kpilot/conduits/knotes/knotes-action.cc:38:35: error: libkcal/calendarlocal.h: No such file or directory

```
A search for **libkcal** at packages.ubuntu.com turns up, among others, the package **libkcal2-dev**, and a browse through the files provided by this package shows that it provides the calendarlocal.h header file.  Try installing this package, e.g.
```

$ sudo apt-get install libkcal2-dev

```

---

### Post by peter_brewer on 2007-04-10
Thanks that really helped.  It turned out I needed to install the KDE-Pim dev package.

This is why I like Ubuntu, people are always friendly.

---

