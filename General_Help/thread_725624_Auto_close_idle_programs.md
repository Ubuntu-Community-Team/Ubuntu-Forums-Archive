---
title: "Auto close idle programs"
date: 2008-03-15
forum: General Help
---

### Post by cro.smiley on 2008-03-15
Is there a way to automaticly close programs that are not being used for some time?
Maybe an application or something that would take care about that...

---

### Post by amingv on 2008-03-16
I don't think there are. It is hard to know when a program is unnecessary. (Some programs will idle for long periods until they receive instructions, but they must be there [e.g. a daemon or your bluetooth syncing program].)

---

### Post by cro.smiley on 2008-03-16
> **amingv said:**
> I don't think there are. It is hard to know when a program is unnecessary. (Some programs will idle for long periods until they receive instructions, but they must be there [e.g. a daemon or your bluetooth syncing program].)

I agree, Well,maybe you could specify what programs should be monitored, like Evince. And if the window hasn't been focused for let's say 30 minutes it is closed.

I'm asking this because i have a problem that most my college materials are in pdf format, and sometimes i just need to look at certain information in them and then forget to close files. And soon i have a bunch of unused documents all over my workspaces...

I could try to develop such application myself but i don't know how to get info about certain window, for how long it hasn't been focused, if that is posible at all...

---

### Post by cro.smiley on 2008-03-31
Any ideas, anybody?

---

### Post by cro.smiley on 2008-07-07
I made a solution for closing some set of applications at the same time.
It's written in java and it takes app names as arguments and trys to kill them. I wanted to have something that will automaticaly close inactive programs, this i have to run manually, but it's also ok for now...

```

import java.io.BufferedReader;
import java.io.File;
import java.io.FileReader;

public class WindowCleaner {

	public static void main(String[] args) throws Exception{
		File proc = new File("/proc");
		File status;
		BufferedReader reader = null;
		if (args.length < 1) System.exit(1);
		
		for (File f: proc.listFiles()){
			if ((status = new File(f,"status")).exists()){
				reader = new BufferedReader(new FileReader(status));
			    System.out.println("Checking process: "+ f.getName());
			    String check = reader.readLine();
			    for (String strKill: args){
			    	
				if (check.contains(strKill)){
					System.out.println("Killing process: "+ f.getName());
					Runtime.getRuntime().exec("kill "+f.getName());
				}
			}
			}
		}
	}
}


```

---

