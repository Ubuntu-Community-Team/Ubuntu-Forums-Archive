---
title: "Blank Java applications in Eclipse"
date: 2007-05-06
forum: General Help
---

### Post by rmx.dave on 2007-05-06
I couldn't think of a better way to title this. I'm writing a Java program in Eclipse that has a GUI, and whenever I try to run the program in Eclipse, it comes up with a correctly sized window, title bar, and then a blank program (see attachment for better explanation). I have Java 1.5 and 1.6 installed (I'm using 1.5 for this project), and I have done all of the check alternatives and Eclipse is using the right JRE, installed right from the repo's.

Does anyone know why it is doing this? I had the same problem back on Dapper and Edgy, but my computer science course moved from applications to applets, and the Applet viewer worked fine, but now we are back to applications for the final exam. I really need help, as I have already procrastinated a lot (due tomorrow), and I will keep messing around trying to fix it. 

Thanks,
Dave

---

### Post by mlind on 2007-05-06
Does the GUI function correctly if launched outside of eclipse?
If it doesn't work outside eclipse either and it's a Swing GUI, then you're not adding your stuff to frame's contentPane.

---

### Post by rmx.dave on 2007-05-06
I just tested it, and no it does not. Does that mean it's my Java version? java -version tells me I'm using 1.5, and I have 1.6 available too, but that one doesn't show the gui either...

EDIT:
Whoops, sorry. I checked, and I am adding the objects to the content pane. This program runs in Eclipse on Windows, at least it did on the campus computers. I just popped it on my flash drive and tried working on it here.

---

### Post by mlind on 2007-05-06
> **rmx.dave said:**
> I just tested it, and no it does not. Does that mean it's my Java version? java -version tells me I'm using 1.5, and I have 1.6 available too, but that one doesn't show the gui either...

Then it sounds like a programming error to me.

---

### Post by rmx.dave on 2007-05-06
That's what I thought too, but it ran on the college computers, using Eclipse there, only that was on Windows...I suppose I could work on it there tomorrow...but I would still like to get this fixed. It has happened with every Java application I've tried running on Ubuntu.

---

### Post by mlind on 2007-05-06
> **rmx.dave said:**
> That's what I thought too, but it ran on the college computers, using Eclipse there, only that was on Windows...I suppose I could work on it there tomorrow...but I would still like to get this fixed. It has happened with every Java application I've tried running on Ubuntu.

Are using Swing or SWT?
If you're using Swing, does this TestGUI display normally?
```

import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class TestGUI extends JFrame {
	private static final long serialVersionUID = 1L;

	public TestGUI() {
		Container c = getContentPane();
		c.setLayout(new BorderLayout());
		
		JTextField field = new JTextField("foo");	
		JButton button = new JButton("dispose");
		button.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				dispose();
			}
		});	
		c.add(field, BorderLayout.CENTER);
		c.add(button, BorderLayout.SOUTH);		
	}
	
	public static void main(String[] args) {
		JFrame.setDefaultLookAndFeelDecorated(true);		
		JFrame frame = new TestGUI();
		frame.setDefaultCloseOperation(WindowConstants.DISPOSE_ON_CLOSE);
		frame.pack();
		frame.setLocationRelativeTo(null);
		frame.setVisible(true);
	}

}

```

If your problem persists, try installing JDK 1.5 from Ubuntu's repository and set
```

sudo update-java-alternatives -s java-1.5.0-sun

```
Then remove all gcj (GNU's java) packages (dpkg -l | grep gcj)

---

### Post by rmx.dave on 2007-05-06
I'll be damned, it was a programming error. Weird, it ran perfectly on a Windows box...but thanks a ton, I've revised my program and now everything is running fine! Again, thanks a ton!

---

### Post by azntfl on 2007-06-30
Hmm I am having this same problem. I am not sure what you mean by programming error? I have a bunch of programs that use GUIs and they all come up blank like in your screenshot. They all used to work in windows :(

---

### Post by mlind on 2007-07-01
> **azntfl said:**
> Hmm I am having this same problem. I am not sure what you mean by programming error? I have a bunch of programs that use GUIs and they all come up blank like in your screenshot. They all used to work in windows :(

Could you post the code then?

---

### Post by azntfl on 2007-07-02
i was able to fix the problem, it wasnt a programming code, its a problem with beryl. I just log on  without beryl whenever i wanna use eclipse.

---

### Post by qamelian on 2007-07-02
> **azntfl said:**
> i was able to fix the problem, it wasnt a programming code, its a problem with beryl. I just log on  without beryl whenever i wanna use eclipse.

It's not a problem with Beryl, it is a known bug in java 1.5 and 1.6. You can correct it by either down-grading to 1.4 or by upgrading to 1.6 update 1.

---

