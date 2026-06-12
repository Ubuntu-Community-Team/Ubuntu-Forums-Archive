---
title: "Ubuntu Crash, Buggy SDL Program"
date: 2008-04-02
forum: General Help
---

### Post by ECoder on 2008-04-02
Hi,

When I'm running a simple piece of C++ code that renders some pixels on the screen using SDL. Ubuntu will totally freeze and there is no way else than reset the system.

I'ts crappy code, and it should not be used because it is constantly trying to access the video-card memory. But how can Ubuntu crash? Why won't CTRL + ALT + BACKSPACE work? I can't access the terminal, how can I recover Ubuntu without rebooting? Its frustrating my to reboot every time I run a buggy script.

```

void DrawPixel(SDL_Surface *screen, Uint8 R, Uint8 G, Uint8 B, int x, int y)
{
    Uint32 color = SDL_MapRGB(screen->format, R, G, B);

    if ( SDL_MUSTLOCK(screen) ) {
        if ( SDL_LockSurface(screen) < 0 ) {
            return;
        }
    }
    switch (screen->format->BytesPerPixel) {
        case 1: { /* Assuming 8-bpp */
            Uint8 *bufp;

            bufp = (Uint8 *)screen->pixels + y*screen->pitch + x;
            *bufp = color;
        }
        break;

        case 2: { /* Probably 15-bpp or 16-bpp */
            Uint16 *bufp;

            bufp = (Uint16 *)screen->pixels + y*screen->pitch/2 + x;
            *bufp = color;
        }
        break;

        case 3: { /* Slow 24-bpp mode, usually not used */
            Uint8 *bufp;

            bufp = (Uint8 *)screen->pixels + y*screen->pitch + x;
            *(bufp+screen->format->Rshift/8) = R;
            *(bufp+screen->format->Gshift/8) = G;
            *(bufp+screen->format->Bshift/8) = B;
        }
        break;

        case 4: { /* Probably 32-bpp */
            Uint32 *bufp;

            bufp = (Uint32 *)screen->pixels + y*screen->pitch/4 + x;
            *bufp = color;
        }
        break;
    }
    if ( SDL_MUSTLOCK(screen) ) {
        SDL_UnlockSurface(screen);
    }
    SDL_UpdateRect(screen, x, y, 1, 1);
}

```

And:
```

while( event.type != SDL_KEYDOWN )
{
    SDL_PollEvent( &event );
    x = rand() % 639;
    y = rand() % 300;
    DrawPixel ( screen, 100, 100, 100, x, y );
}

```

Thank you!

Peter

---

