---
title: "[SOLVED] Microsoft Word Alternatives that work (Compare documents)"
date: 2007-11-01
forum: General Help
---

### Post by gaussian on 2007-11-01
Dear all,

I have been exclusive with different Linux alternatives (with occasional Mac use every once in awhile) for about four years, so I am not a complete Newbie. And my standard line has been that I hate Microsoft products with the exception of Excel and Verdana-font :) I especially have hated Word with a passion and I am still waking up in the middle of the night remembering when my dear spouse's Undergraduate Thesis was being written in Word. Type a letter and wait five minutes with a message "Word is re-paginating your document" flashing (this was 1996).

Now I am currently teaching a college course in a non-computer-related subject. Asking my students to use any other software than Word would be silly (we have a site-license) and would be using my "pulpit" to force down my preferences (LaTeX and Emacs, anyone?) down their throats. They are writing two drafts of a term paper and submitting it electronically to me. I would like a tool with a GUI that would allow me to compare the changes (starting from a .doc file) between the two documents. I am looking for alternatives.

Here is the current situation:

1. Word 2007, running XP inside VirtualBox, does a great job. I take the first draft and the final draft and compare documents to highlight changes. It highlights changes on word-by-word basis, showing me how the document has changed.

2. Antiword+wdiff on command line does the same thing, except the output is not as easy to read and I don't want to spend time writing a macro to convert the output to (say) .tex to make it easy to read again. Too much trouble.

3. Openoffice, Abiword and KWord (versions with Feisty). Either no compare option or it works really badly. Let me use Openoffice as an example: If I have a paragraph where a student has changed couple words and maybe added a sentence, Openoffice will highlight that there is a new paragraph replacing the old paragraph. This is not what I want and is almost completely useless for me. 

Anyone here have any ideas on tools beyond wdiff or Word that could be used to do this? I don't have Windows nor VirtualBox on all the computers I would like to use (not enough memory to run VirtualBox+XP), so tools that work would be appreciated.

Sorry, if this is deemed off topic, and I know that the the title could be viewed as trolling :)

---

### Post by Adam_GUI on 2007-11-01
Is MS Works a viable option for you?
It's only $50 a license and might do what you want.  (Though I'd check at MS's User pages and ask there.)

The only thing you left out is Lotus  symphony.  It's available for Linux and windows.  Might do what you want.  (It's based very loosely on a small percent of OOo's code.)
But I've tested it on my machine and found it hard to navigate and cumbersome to use.

Meh...I'm just spinning my wheels though.  Hope you find something that works.

---

### Post by gaussian on 2007-11-01
> **Adam_GUI said:**
> Is MS Works a viable option for you?
It's only $50 a license and might do what you want.  (Though I'd check at MS's User pages and ask there.)

The only thing you left out is Lotus  symphony.  It's available for Linux and windows.  Might do what you want.  (It's based very loosely on a small percent of OOo's code.)
But I've tested it on my machine and found it hard to navigate and cumbersome to use.

Meh...I'm just spinning my wheels though.  Hope you find something that works.

Thanks. Lotus Symphony was a good suggestion: I am willing to do my homework here. I tried it and found it a) buggy and crashing (which is ok for a Beta), b) slow and c) lacking any document compare (except using track changes on a single document).

I don't think I will give MS Works a try, since I would still have to run it in Windows (or Wine), so I might as well run Word. All ideas are still welcomed, one interesting idea for future classes would be to use Google Documents, but I am not so keen on the potential privacy implications of that.

---

### Post by gaussian on 2007-11-05
Sometimes reading man page can help: if you use wdiff with "-p" option the output is easy to read. While not as fancy as gui-tool a decent document comparison can be done by: 
1. Converting everything (with antiword/pdftotext/similar tools) to text
2. wdiff -a -p student_first_draft.txt student_final_paper.txt

---

