---
title: "Getting tons of errors:  'Sorry, the program &quot;wrapper-2.0&quot; closed unexpectedly&quot;"
date: 2024-04-25
forum: General Help
---

### Post by johann-petrak on 2024-04-25
This is really annoying, I am getting tons of dialog boxes showing that error messages, without any hint of what might be the problem.

Is this a known bug? I really do not think that a program repeatedly crashing like that can be anything but a bug. If the program faces an error,
it should show an error message describing the problem, not just crash. 
Is this known, any idea how to find the causes or how to avoid it?

There is a thread on this forum ([https://ubuntuforums.org/showthread.php?t=2485285](https://ubuntuforums.org/showthread.php?t=2485285)) which is closed which does not have any solutions or suggestions (not sure what the point of locking an unsolved thread is).

---

### Post by TheFu on 2024-04-27
Old threads are closed usually when a spammer starts spamming it. The moderators see that spam and close the thread to prevent cruft in these forums.

Any thread over about a month old becomes less useful to solve an issue, because clearly the person looking for a solution has either moved on or stopped providing answers to question or didn't follow through with prior suggestions.

Sometimes there isn't any good answer either.

These forums don't work like others were lots of people add "me too" for similar issues.  1 issue per thread for 1 person. This is because each of our needs and computers are special, needing a customized answer.  Now, if someone finds an existing thread helps them solve their problem, that's fantastic.  But based on history, we know that systems are seldom identical and slightly different answers are needed for each individual and each computer.

Nobody can help with the issue you've posted. No OS listed. No version listed. No DE listed. No description of what you were doing at the time listed.  Did you look at the system log files for the time to see what they say?  That's the 1st step in seeking answers for any problems on Unix-like OSes.  Linux isn't MacOS or MS-Windows. 

If you want to complain, that's find. Have at it.
If you are interested in help solving the problem, answer the questions asked and check the system logs.

---

### Post by Holger_Gehrke on 2024-04-27
If you're talking about '/usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0', then that's a program for running the panel-plugins found in '/usr/lib/x86_64-linux-gnu/xfce4/panel/plugins/'. Those are published as shared objects (*.so) and can't be run on their own (as i already said in the thread you're linking to). It's a lot more likely that it's the plugin crashing than the wrapper; but the wrapper is the owner of the process and apport (the crash reporting system) can't really tell all the wrapper processes apart (There's quite a few of them, as I'm writing this there are eight xfce-panel-plugins running on my system). One method to find out which plugin is the problematic one would be to generate a list of all the plugins running (ps ax| grep '[w]rapper-2.0'>listOfPlugins.txt) when you start working. After a crash occurs, generate another list and compare the two. 

Holger

---

### Post by InuY4sha on 2024-11-18
@Holger_Gehrke I can get the list but the crash is right at boot. do you know how to get the list of the  plugins that are "SUPPOSED" to be running to compare against those?Is there a config file where these plugins list is defined?
I can't really tell what is not running..

---

### Post by john6443 on 2024-11-18
It&#8217;s definitely frustrating to deal with repeated crashes and cryptic error messages without a clear cause or solution. Based on your description, it sounds like the program you're dealing with may not be handling errors gracefully, which is indeed a flaw in its design.  

[B]Is This a Known Bug?  
[/B]Yes, issues like this are fairly common, especially with programs that rely on complex dependencies like PipeWire, JACK, or other system services. The error messages you're seeing might not directly relate to the actual cause but could indicate a deeper issue with configurations or missing dependencies. If you&#8217;re encountering constant dialog boxes without proper logs or debugging options, it could indeed be a known bug or an unaddressed issue within the application.  


[B]How to Diagnose the Problem:  
[/B]

[B]1. Check System Logs:  
[/B]   Use `journalctl` to capture detailed logs related to the crashing program. For example:  
   ```bash
   journalctl -xe | grep [program_name]
   ```  
   Replace `[program_name]` with the crashing program&#8217;s name.  


[B]2. Update the Program:  
[/B]   Ensure you&#8217;re running the latest version of the program. Many bugs are fixed in subsequent updates. Run:  
   ```bash
   sudo apt update && sudo apt upgrade
   ```


[B]3. Look for Dependencies:  
[/B]   Some crashes occur due to missing or incompatible libraries. Check if the program has additional dependencies you need to install.  


[B]4. Check Related Services:  
[/B]   If the program relies on services like PipeWire, PulseAudio, or JACK, ensure these are running and properly configured.  


[B]5. Community Resources:  
[/B]   If you haven&#8217;t already, explore other forums or GitHub issues pages for the program. While the thread on Ubuntu Forums you mentioned is locked, platforms like Stack Overflow or GitHub are more actively monitored.  


[B]6. Temporary Workarounds:  
[/B]   If the crashes persist and the program isn't critical, consider switching to an alternative tool. You could also suppress error dialogs temporarily by disabling problematic modules (if that&#8217;s an option).  


[B]Tools to Help Diagnose Issues:  
[/B]

For example, on my site, ([https://toolzel.com)]("https://toolzel.com)**"), I provide free tools and resources to tackle various technical challenges. You might find useful utilities there, like log analyzers or configuration checkers, that can help you get to the root of such issues.  


Let me know if you need more specific steps tailored to the program you&#8217;re using!

---

### Post by Holger_Gehrke on 2024-11-18
> **InuY4sha said:**
> @Holger_Gehrke I can get the list but the crash is right at boot. do you know how to get the list of the  plugins that are "SUPPOSED" to be running to compare against those? Is there a config file where these plugins list is defined?
I can't really tell what is not running..

The list of plugins is stored in xfconf,  a hierarchical configuration storage system similar to dconf, gconf or the Windows registry. There is a channel named 'panels' with sub-channels named 'panel-{0..n}'. Each of these sub-channels has an item named 'plugin-ids' which holds a field with plugin-numbers. The plugins themselves each have a channel of their own named 'plugin-n' with n being the plugin-number as used in 'plugin-ids'. You can see this using either xfce4-config-editor (GUI) or you can directly look at the xml-file '~/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml' (xfconf uses human-readable XML for storage, IMHO a better idea than the various binary formats used by other configuration storage systems).

Holger

---

