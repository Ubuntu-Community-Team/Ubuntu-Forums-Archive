---
title: "not declared in declare in this scope???"
date: 2007-11-03
forum: General Help
---

### Post by thhuang on 2007-11-03
Hi , 

I tried to run the below coding in ubuntu but it prompt me an error  :
"In function ‘int main()’:
Task1.cpp:44: error: ‘execute_command’ was not declared in this scope
"

I cant find what is the cause, can any one help??


#include <stdlib.h>
#include <stdio.h>
#include <unistd.h>
#include <sys/types.h>
#include <string.h>

#define MAX_INPUT_SIZE 100
#define MAX_ARG   50

//Tracker for display start up message
int displayMsg=0;

int main()
{
	char line[MAX_INPUT_SIZE+1];
	int n, retcode=1;

// Add in instructions to prompt user what to do
	if(displayMsg==0){
		printf("Type in some commands for example 'pwd', 'ls', 'ps', 'quit'\n");
	}

	do {
		/* display the prompt i.e.$ */
	 	printf("MYUNIXXX>>>");

		/* obtain input from the standard input i.e. keyboard input*/
	 	fgets(line, MAX_INPUT_SIZE, stdin);
    	
		/* this is to get rid of the CR/LF */
		n = strlen(line);
		line[n-1]='\0';
		/*printf("%s",line);*/

		/* exit the loop if "quit" command is entered */
		retcode = strcmp(line, "quit");
		if (retcode ==0) {
			printf("Bye ... see you again\n");
		} else {
			[COLOR="Red"]execute_command(line);[/COLOR]		}

	} while (retcode !=0);
}

int execute_command(char *cmd)
{
	pid_t  pid;
	int i=0;

	/* create a copy of process */
	pid = fork();

	if (pid > 0){ // parent copy ... wait for child process to complete 
		//wait((int *) 0);
	} else if (pid == 0){ // child copy ... execute the command 
		/* execute the command here ... should never come back */

//If execlp return, it will display a invalid msg, user try again
		i = execlp(cmd, cmd, NULL);
		//i = system(cmd);
		if (i!=0)
			printf("You have enter an invalid command\n");
			displayMsg=1;
			exit(-1);
			main();
	} else{ // error in fork() call
		printf("<err> error in executing the command\n");
		return(-1);
	}
}

---

