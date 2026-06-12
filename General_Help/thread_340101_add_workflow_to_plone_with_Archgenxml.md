---
title: "add workflow to plone with Archgenxml"
date: 2007-01-16
forum: General Help
---

### Post by tonydevlin on 2007-01-16
I have been trying to add a UML workflow model to a Plone website, with the help of ArgoUml
I have been using following the website:
[http://plone.org/documentation/tutorial/anonymously-adding-custom-content-types-with-argouml-and-archgenxml/creating-a-class-and-workflow-with-argouml](http://plone.org/documentation/tutorial/anonymously-adding-custom-content-types-with-argouml-and-archgenxml/creating-a-class-and-workflow-with-argouml)
I have created all of the model that it suggests and I am getting confused at stage 9, which says:
"Now, save this file as "ProcessImprovement.zargo".  Pull up a command prompt and navigate to that directory.  Make sure that you've added the ArchGenXML directory to your env path, and type the following:C:\Sandbox\Plone\Tutorial>ArchGenXML.py ProcessImprovement.zargo"

I have saved the file in the location:
C:\Documents and Settings\Tony\My Documents\Test\ProcessImprovement.zargo
In the directory Test appart from the ProcessImprovement file, I also have saved; argouml_profile.xmi and an ArchGenXML directory, which on the website it recomends you to add them in.  When I pull up a command prompt:  C:\Documents and Settings\Tony\My Documents\Test>ArchGenXML.py ProcessImprovement.zargo
This brings up a message 'ArchGenXML.py' is not recognised as an internal or external command, operable program or batch file.  
This I think is because ArchGenXML.py is in the directory ArchGenXML.  So I have also tested this out by cut and paste the ProcessImprovement.zargo file from the Test folder into the ArchGenXML folder. I then ran the command:
C:\Documents and Settings\Tony\My Documents\Test\ArchGenXML>ArchGenXML.py ProcessImprovement.zargo
This printed the line "CRITICAL Hey, we need to be passed a UML file as an argument!"
Then below this is printed out loads of commands, like <b>usage</b> "ArchGenXML.py [options] <xmi-source-file> [output directory], <b>options</b>, <b>configuration file options</b>...etc....
I have also been on System Properties (right click on My Computer) -> advanced ->Environment Variables and int the path option appended on the path to the file ArchGenXML.py and this still had no effect.  Am I entering in the command correctly? Or have I not organsied the files out correctly and how do I put the ArchGenXML directory in the correct path like it says, or is it something competly different that I am doing wrong.

Would be very greatful for your help.  Thanks.
I have uploaded the file with this message so that you know how I have set out my files, in the files I have left it in the original way with the ProcessImprovement.zargo file outside of the ArchGenXML directory.

---

