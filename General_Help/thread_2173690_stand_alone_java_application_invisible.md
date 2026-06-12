---
title: "stand alone java application invisible"
date: 2013-09-10
forum: General Help
---

### Post by geoffrussell on 2013-09-10
I'm running Ubuntu 12.04.3 LTS on a Shuttle slim pc  Atom D2550 with GMA 3650 graphics, using Unity 2D because
the Cedartrail DRM stuff doesn't work with the latest kernels.

I've tried jdk1.7.0_25 from Oracle &  openjdk-6 & openjdk-7 and a very basic "GUI Hello World" application doesn't show
on the screen ... the program compiles and runs and the java log appears in the launcher but nothing on the screen. 

The program is below ... dead simple ... it works fine on my more conventional desktop also running 12.04.3 LTS.

Any ideas?

Cheers,
Geoff Russell

import javax.swing.*;
public class HelloJava
{
  public static void main( String[] args ) {
    JFrame frame = new JFrame( "HelloJava" );
    frame.add( new HelloComponent() );
    frame.setSize( 400, 300 );
    frame.setVisible( true );
  }
}
class HelloComponent extends JComponent {
    public void paintComponent( java.awt.Graphics g ) {
    g.drawString( "This is my Hello, Java!", 125, 95 );
    }
}

---

### Post by geoffrussell on 2013-09-11
Since posting this thread I've noticed that jconsole doesn't work either ... running jconsole from the command line produces nothing, no error messages, no popup, nothing.

---

### Post by 1clue on 2013-09-11
Do you have JAVA_OPTS defined in your environment?  Does one of the options contain "headless"?

Also, are you running the server jvm or the regular one?

---

### Post by geoffrussell on 2013-09-12
Hi 1clue, thanks for replying.

No JAVA_OPTS isn't defined. 

Sorry, I'm a Java novice and don't understand the second question. JAVA_HOME points to /home/geoff/Downloads/jdk1.7.0_25 and the java/javac/jconsole executables
are in $JAVA_HOME/bin

I started off just using apt-get install for java 7 and eclipse so that I could learn java. Then when things didn't work I downloaded the Oracle jdk. Still without success.  Non-graphical
code works!

Cheers,
Geoff

---

### Post by geoffrussell on 2013-09-12
P.S. eclipse seems to work fine ... no obvious problems.

---

### Post by leg on 2013-09-12
Could it be because you are using JComponent. I have always used JPanel in that situation. JComponent is at the top of the hierarchy and is provides inhertied members for all subclasses. Try switching JComponent for JPanel and see what happens.

Also from the [Java tuts]("http://docs.oracle.com/javase/tutorial/displayCode.html?code=http://docs.oracle.com/javase/tutorial/uiswing/examples/components/FrameDemoProject/src/components/FrameDemo.java"):
```
package components;
 
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
 
/* FrameDemo.java requires no other files. */
public class FrameDemo {
    /**
     * Create the GUI and show it.  For thread safety,
     * this method should be invoked from the
     * event-dispatching thread.
     */
    private static void createAndShowGUI() {
        //Create and set up the window.
        JFrame frame = new JFrame("FrameDemo");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 
        JLabel emptyLabel = new JLabel("");
        emptyLabel.setPreferredSize(new Dimension(175, 100));
        frame.getContentPane().add(emptyLabel, BorderLayout.CENTER);
 
        //Display the window.
        frame.pack();
        frame.setVisible(true);
    }
 
    public static void main(String[] args) {
        //Schedule a job for the event-dispatching thread:
        //creating and showing this application's GUI.
        javax.swing.SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                createAndShowGUI();
            }
        });
    }
}
```
Note no JComponent.

---

### Post by geoffrussell on 2013-09-12
Thanks Leg.  But the code comes from "Learning Java" and runs perfectly well on two other machines running 12.04 Ubuntu. It
isn't the code.

---

### Post by leg on 2013-09-13
Well I tried your code exactly as it is in your post and I got a visible window so I am not really sure what your problem is. Sorry.

---

