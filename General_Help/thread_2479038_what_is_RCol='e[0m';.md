---
title: "what is RCol='\e[0m';"
date: 2022-09-12
forum: General Help
---

### Post by raleigh3 on 2022-09-12
What is
RCol='\e[0m';
doing?

#!/bin/bash
# 
# Colors

Red='\e[0;31m';     
BRed='\e[1;31m'; 
BIRed='\e[1;91m';
Gre='\e[0;32m';     
BGre='\e[1;32m';
BBlu='\e[1;34m';
BWhi='\e[1;37m';
RCol='\e[0m';


  echo -e "
${BGre}ubuntu-gdm-set-background script (for changing Ubuntu ${BWhi}20.04${RCol} GDM Background) 

there are four options

1. background with gradient vertical ( requires two valid hex color inputs)${RCol} "

---

### Post by &amp;KyT$0P# on 2022-09-12
It is defining a variable containing the ANSI escape sequence to clear the effect of all previous ANSI escape sequences that define formatting (colors, underlining, etc).

---

