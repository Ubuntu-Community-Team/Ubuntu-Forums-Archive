---
title: "Eclipse and Java 6 help"
date: 2007-08-31
forum: General Help
---

### Post by jazzdonkey on 2007-08-31
Hello,

I am currently using Ubuntu 7.04.  It is a fresh install along with eclipse and Java JDK 6.0.  When I was messing around with it the other day I imported the Scanner class but when I went to define a Scanner object eclipse got pissed at me and said "the type 'Scanner' cannot be resolved".  Anyone have any suggestions?  Did I miss something?  Thanks ahead of time.

---

### Post by tszanon on 2007-08-31
> **jazzdonkey said:**
> Hello,

I am currently using Ubuntu 7.04.  It is a fresh install along with eclipse and Java JDK 6.0.  When I was messing around with it the other day I imported the Scanner class but when I went to define a Scanner object eclipse got pissed at me and said "the type 'Scanner' cannot be resolved".  Anyone have any suggestions?  Did I miss something?  Thanks ahead of time.
Could you please post the code?

---

### Post by jazzdonkey on 2007-08-31
No problem.  Just to let you know I am beginning to write in java with no other programming experience, so there are probably a lot of mistakes and it probably looks bad, etc...

```

//January 24, 2007
//Interest Calculator (Practice)

import java.util.*;

public class interestCalculator {

	public static void main(String[] args) {

		/*
		 * Why not gather some info from the user? I'll get their name and ask
		 * if they would like to run the program.
		 */
		
		Scanner stdin = new Scanner(System.in);
		System.out.print("Please state your first name: ");
		String firstName = stdin.nextLine();
		System.out.print("Please state your last name: ");
		String lastName = stdin.nextLine();
		String name = firstName + " " + lastName;
		System.out.print("Hello " + name
				+ ", would you like to run the Interest Calculator? ");
		String startInput = stdin.nextLine().trim().toLowerCase();

		/*
		 * Check for common entries and direct the entries to the appropriate
		 * areas of the program.
		 */
		
		if (startInput.equals("exit") || startInput.equals("no")
				|| startInput.equals("quit") || startInput.equals("n")
				|| startInput.equals("end")) {
			String output = ("I'm afraid. I'm afraid, " + firstName + " .\n"
					+ firstName + " , my mind is going. I can feel it. I can feel it. \nMy mind is going. There is no question about it. I can feel it. I can feel it. I can feel it. \nI'm a... fraid.");
			System.out.println(output);
			System.exit(0);
		} else if (startInput.equals("yes") || startInput.equals("continue")
				|| startInput.equals("go") || startInput.equals("start") || startInput.equals("y")) {
			
			/*
			 * After checking and redirecting, it's time to obtain the loan
			 * information
			 */
			
			do {
				System.out.println("");
				System.out.print("Enter current principal amount: ");
				double principal = stdin.nextDouble();
				System.out.print("Enter your APR (7.6 = %7.6): ");
				double rate = stdin.nextDouble();
				System.out.print("Enter current monthly payment: ");
				double payment = stdin.nextDouble();

				/* convert some of the user's input and simplify */
				
				double monthlyPrincipal = principal/12;
				
				double yearlyPayment = payment * 12;
				final double monthlyPayment = yearlyPayment/12;
				
				double yearlyInterestRate = 1 + (.01 * rate);
				final double monthlyInterestRate = yearlyInterestRate/12;
				
				double yearlyTotal = (principal - yearlyPayment) * yearlyInterestRate;
				double monthlyTotal = yearlyTotal/12;

				double compoundedInterest = yearlyTotal * yearlyInterestRate;
				
				double months = 0;
				double years = months/12;
				
				/* start a counter to figure the years of payback */
				
				do {
					yearlyTotal = (yearlyTotal - yearlyPayment) * yearlyInterestRate;
					years++;
					
					
				} while (yearlyTotal > 0);
				
				/* time to dish out the info to the user */

				System.out.println("");
				System.out.println("It will take approximatley " + years
						+ " years");
				
				/* run again? */
				
				System.out.println(" ");
				stdin = new Scanner(System.in);
				System.out.print(firstName + " ,would you like to run again? ");
				startInput = stdin.nextLine().trim().toLowerCase();
				System.out.println("");
				
				/* error checking */
				
			} while ((startInput.equals("yes") || startInput.equals("continue") || startInput
					.equals("go") || startInput.equals("y")));

			if (startInput.equals("exit") || startInput.equals("no")
					|| startInput.equals("quit") || startInput.equals("n")) {
				String output = ("I'm afraid. I'm afraid, " + firstName
						+ " .\n" + firstName + " , my mind is going. I can feel it. I can feel it. \nMy mind is going. There is no question about it. I can feel it. I can feel it. I can feel it. \nI'm a... fraid.");
				System.out.println(output);
				System.exit(0);
			}
		}
	}
}

```

Hope this helps.  Do you think it has something to do with the JRE I'm using?  I think it's 1.4.2.

---

### Post by jazzdonkey on 2007-08-31
Okay,  Stupid mistake on my part!  I was looking at the JRE as I was replying and realized that since I was using 1.4.2 that was why it was acting up.  I switched it to Java-6-sun-1.6.0.00 and that solved it.  Thanks for the quick reply!

---

### Post by tszanon on 2007-08-31
Good to know you could solve your problem...I was about to compile the code myself and see the error messages to start to think about what could be wrong. Since I use jdk1.6, there would be no errors, and I believe I would be lost. :)

Happy learning with the new language! :)

---

