---
title: "Problem with uppercase input using pygame"
date: 2016-01-18
forum: General Help
---

### Post by mitmag on 2016-01-18
Well folks, it seems I have another problem with pygame! I am trying to get user input
for an Address book I am working on. I can't seem to be able to gather the uppercase
keys properly. I have tried the info from the docs, but have not had any luck. Hope someone out
there can help me.

From the docs I have been trying to get the following code to do the job:

if pygame.key.get_mods() & pygame.KMOD_LSHIFT:

This line of code will produce uppercase but will also print LSHIFT on the screen
when I try to input an uppercase letter.
This seems to be my problem. I have worked for days on this and finally decided
to start from scratch again!

Following is my current code:

#display_text.py

import pygame
import time
from pygame.locals import *

BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
RED = (255, 0, 0)

pygame.init() 
screen = pygame.display.set_mode((640,480))
font = pygame.font.Font(pygame.font.get_default_font(), 15)
text = font.render("",True,BLACK)
currenttext = ""
running = 1
while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT: 
            running = 0
            pygame.quit()
        elif event.type == pygame.KEYDOWN:
            if len(currenttext) <= 80:
                if event.key == pygame.K_BACKSPACE:
                    currenttext = currenttext[:len(currenttext)-1]
                    screen.fill((0,0,0))
                    text = font.render((currenttext),True,GREEN)
                    screen.blit(text,(10,30))
                    pygame.display.flip()
                elif event.key == pygame.K_ESCAPE:
                    running = 0
                    pygame.quit()
                else:
                    key = pygame.key.name(event.key)
                    currenttext += key
                    text = font.render((currenttext),True,GREEN)
                    screen.blit(text,(10,30))
                    pygame.display.flip()

This seems to work fine for lowercase, numbers and the ESCAPE key.
I need to add code to gather uppercase, but I have problems doing so.
If someone knows how to do this I would greatly appreciate your help.
Thanks in advance!

---

