---
title: "Way to pretty-up java apps?"
date: 2005-10-27
forum: General Help
---

### Post by sailor420 on 2005-10-27
Is there a way to make java apps look a bit better, similar to the way you can tweak QT apps? I've got several java-based programs, and they all have that standard, nasty java look. Any ideas?

---

### Post by JOKe on 2005-10-27
the bad idea that i have is this :
install jre 1.5.0 this will add a new oceanic look and feal by default in your java apps its nice and blue


good idea: ( or bad...dont know :) )
if you want the java programms to look like in QT or GTK ( if you use KDE or Gnome ) make this :
open the mainClass.java in the java Program  ( this is the class (java fail) where is located the "public static void main(String[] args )" funktion and add this : 
public static void main(String[] args ){
//from here :  
try {
                UIManager.setLookAndFeel(UIManager.
                                         getSystemLookAndFeelClassName());
            } catch (UnsupportedLookAndFeelException ex) {
System.out.println("My Fucking LookAnd Feel is unsupported");
            } catch (IllegalAccessException ex) {
System.out.println(Illegal Bullshits ");
            } catch (InstantiationException ex) {
            } catch (ClassNotFoundException ex) {
System.out.println("lOL :) ");
            }
//to here
....here is the code wich is from the application......... dont edit it :)
}


the other think you must add in this file is the import declaration : 
import javax.swing.UIManager; 

at the top  where are other imports


this must get the look and feel that you use adn apply it to your java program
if this dont work you can try  : UIManager.setLookAndFeel(UIManager.
                                         getCrossPlatformLookAndFeelClassName()); 


but i think the first one was the right.







p.s. Anti Aliasing will not work.





this will not work on all programs
there is 3 good visual java APIs :) 
the first one Swing - the most used - this will work;
you can gues it by the class names : they are not Button , TextField and etc they are JButton , JTextField , JTextArea J****.
the other is AWT - most used for applets - if the apps dont like it ... you cant do anythink :(
the other SWT - the newest API it is provided by eclipse fundation supported by IBM it uses the native components and the native look and feel so you will not have troubles under GTK / Windows .. if there is a trouble with look and feel in QT ( KDE ) i dont have KDE and i dont know but if it have and if some java app used it : try to ask somewhere in eclipse.org

---

