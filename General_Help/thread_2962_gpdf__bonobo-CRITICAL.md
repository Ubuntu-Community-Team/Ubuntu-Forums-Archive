---
title: "gpdf / bonobo-CRITICAL"
date: 2004-11-02
forum: General Help
---

### Post by drunken-wallaby on 2004-11-02
hi there. i'm currently facing the following problem. opening some pdf-documents with gpdf results in opening gpdf however not displaying the document. when i open a document via the console ```
gpdf mydocument.pdf
``` i get the following errors: ```
(gpdf:21559): Bonobo-CRITICAL **: file bonobo-widget.c: line 325 (bonobo_widget_get_control_frame): assertion `BONOBO_IS_WIDGET (bonobo_widget)' failed

(gpdf:21559): Bonobo-CRITICAL **: file bonobo-control-frame.c: line 571 (bonobo_control_frame_set_autoactivate): assertion `BONOBO_IS_CONTROL_FRAME (frame)' failed

(gpdf:21559): Bonobo-CRITICAL **: file bonobo-widget.c: line 325 (bonobo_widget_get_control_frame): assertion `BONOBO_IS_WIDGET (bonobo_widget)' failed

(gpdf:21559): Bonobo-CRITICAL **: file bonobo-control-frame.c: line 533 (bonobo_control_frame_control_deactivate): assertion `BONOBO_IS_CONTROL_FRAME (frame)' failed
```so i want to ask if this is a gpdf bug or if someone knows how to resolve this issue. opening the document with xpdf works fine, though :)

thanks for your help.

---

### Post by diebels on 2004-11-02
I don't get this. Do you have latest 2.8.0-0ubuntu1 version of gpdf? Is it with all or some pdf documents?

---

### Post by drunken-wallaby on 2004-11-02
[QUOTE=diebels]I don't get this. Do you have latest 2.8.0-0ubuntu1 version of gpdf? Is it with all or some pdf documents?[/QUOTE]

hi diebels. thanks for your reply. i only get this error with some documents. i can't figure out however, why the error occurs only for certain pdf files while gpdf can open other documents without any problem.

and yes, i'm running the latest version of gpdf provided by ubuntu...

---

