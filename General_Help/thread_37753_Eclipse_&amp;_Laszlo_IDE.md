---
title: "Eclipse &amp; Laszlo IDE"
date: 2005-05-28
forum: General Help
---

### Post by Txukie on 2005-05-28
Hello, im new in the forum and first of all i would like to say hi to the community.
Ive been using ubuntu hoary for some time now, and its the first linux distro that ive used exclusively (no windows installed). Im a web designer that struggles to develop under linux because of  the lack of "comfortable" apps. So ive got dreamweaver MX installed under crossover office. Looking on the net i found this rich-application internet program called Laszlo for creating interfaces that use the Macromedia Flash plugin. It seemed ideal for me. Ive done a few programs under vi but wanted to move on to a more friendly IDE for developing. I saw eclipse had a plugin for laszlo called laszlo IDE. Ive got eclipse 3.0.2 and laszlo presentation server 3.0 with the GEF-SDK-3.0.1 and EMS-SDO-XSD-SDK latest version. I start LPS with
```
sudo /opt/lps-3.0/Server/tomcat-5.0.24/bin/startup.sh
``` 
and starts just fine
Then i start Eclipse with
```
/opt/eclipse/eclipse -clean -vmargs -Dorg.eclipse.swt.browser.internal.flash
``` 
and it loads fine too.
The problem is when i create a laszlo project and a laszlo file inside of it i dont see any palette. I get a "no palette available" error. Plus i dont seem to get any color help on my xml editing. Any help would be greatly appreciatted. Cheers

---

### Post by ltmon on 2005-05-28
As for the Lazlo stuff, I have no idea because I've never used it -- although it does look like a good toolkit in many ways.  I believe it could be based on XUL (the same markup Firefox uses to do it's user interface) so you could have some success looking for XUL editors.

As for XML not being hilighted, this is because out of the box Eclipse is fairly bare bones.  You should search for an XML plugin for Eclipse.  Two popular ones are [oXygen](http://www.oxygenxml.com/) and [XMLBuddy](http://xmlbuddy.com/).  I think they're both commercial with free (trial? non-commercial only?) versions available.

---

### Post by Txukie on 2005-05-30
Reading the IDELaszlo Documentation it says that should implement syntax highlight by itself. Thank you for your answer but still haven't managed to make it work ](*,)  ](*,)  ](*,) 
Anybody???

---

### Post by l.tambiah on 2005-05-30
Txukie,

> Ive been using ubuntu hoary for some time now, and its the first linux distro that ive used exclusively (no windows installed). Im a web designer that struggles to develop under linux because of the lack of "comfortable" apps.

I was a windows user once too, partly due to being forced to use it during my undergraduate years. I to enjoy web design programming and creating. Dreamweaver is a great tool, and i was once a great fan of the software. However i believe there are some great web tools in the Linux world too such as Bluefish and NVU. I dont think as web designers we are less fortunate due to one piece of software. Dreamweaver can teach bad habits such as relying on GUI rather than understanding code behinnd it. Writing our own code we can concentrate on writing it towards W3C (World Wide Standards). The trick is really is to understand there are altenatives, its a case of making a switch. As for good design and dynamic content it is all up to the programmer the power is in your hands. Google is a fine example of web design/development which has been purely engineered using python on Linux. There is great opportunities in web development for Linux in my opinion. 

Laszlo Application

I too have came across Laszlo, i have to say im pretty impressed, and playing with it quite happily. I have configured the Eclipse environment for Laszlo where i  see a palete and get a preview all within the eclipse environment. 

Not sure what your problem could be here, may i suggest you try and install the plugins etc again. I do have my pallete working so at least you know this can work.

Also when u begin Eclipse i dont use the -clean option, so try using the following:

```
/opt/eclipse/eclipse -vmargs -Dorg.eclipse.swt.browser.internal.flash
``` 

However i dont think this would make much difference. Im new to Laszlo myself so learning as you are. Try posting a request to the IBM Laszlo forum, or Laszlo forum if you havent done already. 

I personally think using vim and compiling the Laszlo code to view in the browser isn't really to much of a pain either. Whilst we must also realise that the Laszlo plugin for Eclipse is not yet mature. 

Try this link it may give you some pointers:- [Laszlo Link](http://www-106.ibm.com/developerworks/forums/dw_expandTree.jsp?thread=80278&forum=412&cat=28&message=13714563) 
 
Regards 

L. Tambiah

---

### Post by Txukie on 2005-05-31
Thanks for your reply.
I must first say that about Dreamweaver what i mainly like is its appearence and ease of use, but i always code and never use the WYSIWUG environment, i like programming :smile: !
Ive personally tried NVU and have to say that its a very nice program, which im really expecting to become something great, but for today its still a bit too limited for me. The PHP support is just too poor, though i really like the idea of having W3C standards finally followed by a program (watch and learn frontpage :roll: )
Anyways about Laszlo i too was very impressed, and very happy to learn that Eclipse had a plugin. Ive tried installing and uninstalling it many times with different versions but none of them seemed to work.
I guess i can still use vim but would like to use something a bit more friendly during my "learning time".
I hope you can help me by just telling me what version of java, eclipse, laszlo, laszloIDE and other plugins you use and a rough how-to on how u install it. It would be greatly appreciatted \\:D/  \\:D/

---

### Post by l.tambiah on 2005-06-01
Okay i will install my environment at home and reinstall, to show you what i did to make this application working. Please bear with me, i've got quite a lot on at minute, however i will try and do this for you today.

---

### Post by Txukie on 2005-06-01
Cheers mate ill be waiting! :-P

---

### Post by l.tambiah on 2005-06-02
**Package Requirements**

[I]
J2SE Development Kit (JDK) 5.0 update 3

Eclipse 3.0.2

Mozilla -1.6 [Get Mozilla-1.6 here](http://www-106.ibm.com/developerworks/forums/dw_thread.jsp?thread=81299&forum=412&cat=28) 

You require mozilla to make the preview work. You must also install flash in the mozilla browser.** Firefox will not work!!!**

openlaszlo-3.0


[/I]

**Java Environment**

1.Install the J2SE Development Kit (JDK) 5.0 update 3 from [Java 1.5.0](http://java.sun.com/j2se/1.5.0/download.jsp) 

2.Set the classpath (i take it you know how to do that).

**Linux Install Considerations For Laszlo and Eclipse**

The Visual Editor uses the SWT Browser control, which requires Linux users to install Eclipse 3.02 and Mozilla 1.6.x (Note: Mozilla Firefox will NOT work) for the IDE to function correctly. Here are the steps to follow:

1.Download and install Eclipse 3.02. 

2.Download and install Mozilla 1.6 

3.Once Mozilla 1.6 is installed: 

check if the shell variable MOZILLA_FIVE_HOME is set and points to Mozilla 1.6. 

$ echo $MOZILLA_FIVE_HOME
If necessary, set correctly by doing: 

$ MOZILLA_FIVE_HOME=<Mozilla 1.6 install directory>
$ export MOZILLA_FIVE_HOME

4.Startup eclipse by doing the following; 
$ cd <Eclipse 3.02 install directory> 
$ ./eclipse -vmargs -Dorg.eclipse.swt.browser.internal.flash

(This will enable the Flash Player in the SWT Browser) 

6.Put eclipse to your required directory i.e home/username/myprograms/eclipse

7.Test Eclipse, to make sure its functioning then close the application.

8.Extract the laszloIDE.zip file, rename folder to “lasloIDE”

9.Open Eclipse, From the Eclipse menu, click "Help -> Software Updates -> Find and Install...". Select "Search for new features to install".

10. Create a "New Archived Site..." pointer to the downloaded folder we created in step8.

11. Click the checkbox next to the new "laszloIDE.zip" site pointer to select all four site components, then click "Next". You may get a "Integrity Personal Policy Alert" message from Windows warning about executing java. If so, then accept this message.

12. Click "Select All" to select all five features, then click "Next".

13. Persue the licenses, click "I accept the terms in the license agreements", then click "Next".

14. Each feature is downloaded. Click "Install" for each feature (five times). Be patient, as the Eclipse download server can be slow at certain times.

15. Restart Eclipse as the last step. (By clicking "Yes").

16. Extract the lazslo server file “openlaszlo-3.0-unix.tar.gz”

17.Add the directory lps-3.0 to your required location.

18. Run the server in bash, change directory  i.e 
/home/username/myprograms/lps-3.0/Server/tomcat-5.0.24/bin

19. In Bash type ./startup.sh

20. Your server should now be running. 

21. Repeat step 3 if necessary.

22. Startup eclipse by doing the following; 

$ cd <Eclipse 3.02 install directory> 
$ ./eclipse -vmargs -Dorg.eclipse.swt.browser.internal.flash

23. In eclipse environment goto Window>Preferences and select Laszlo at the left hand side.

24.For LPS Web Root set it to  ....../lps-3.0/Server/lps-3.0 you can use browse for this.

25. You should notice the “context root” has now changed to lps-3.0.

26.For web browser location you need to point it to the mozilla 1.6 which was installed earlier. In my case this is /usr/local/mozilla/mozilla

27.Click Apply

28. Goto Window>Customize Perspective and check the Laszlo and click ok.

29.Note:The Laszlo Presentation Server must be running in order for the design view to work. 

30.From the Eclipse menu, click "File -> New -> Project...". Select "Laszlo -> Laszlo Project". 

31.You may also be prompted to switch to the Laszlo perspective, and you should do so. 

32.The first time you create a Laszlo project, you will be prompted for the location of the Laszlo Presentation Server. 

33.Expand your newly created Laszlo Project in the left-hand Navigator window. Select the src folder. Right-click on the src folder and click "New -> Laszlo File". Click "Finish". 

34.Drag and drop a component (such as button) from the right-hand Palette window into the <canvas> tag. Then, type a string such as "Hello World!" inside your new tag (for example, <canvas><button>Hello World!</button></canvas>) 

35.Try using xml code assist (ctrl+space) for xml elements and attributes. 

36. Switch to the design tab and see what it looks like. 

37. Click on the component, and drag on the corners of the item to resize it, or drag on the top middel to move the component. 

38. Save your Laszlo file. 

39. From the Eclipse menu, click "Run -> Run...". Select "Laszlo Application" and "New". Select your project, and enter a file path (i.e. /src/new_file.lzx)

40. You should see your test file when you click "Run".

You may want to consider setting MOZILLA_FIVE_HOME permanently
to do this add the following code to the end of the file:

$ /home/username/.bashrc

MOZILLA_FIVE_HOME=/your/mozilla/directory
export MOZILLA_FIVE_HOME 

And there you have it, mine works as it should.  Hope this works for you...

---

### Post by Txukie on 2005-06-04
Sorry to take so long to answer, had a kernel panick and had to reinstall everything, went for a Debian Sarge this time. Everything is working now fine thanks to your help. Thanks a lot, now i'll begin practicing :grin:  :grin:  :grin:

---

