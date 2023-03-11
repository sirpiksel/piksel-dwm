dwm - dynamic window manager
============================
dwm is an extremely fast, small, and dynamic window manager for X.

This is my personal dwm config + some applied patches from https://dwm.suckless.org/patches/

Patches
-------
```
alwayscenter
barpadding
fullgaps
monoclesymbol
activetagindicatorbar
warp
integrated status text
```

Theme
-----
```
static const unsigned int borderpx  = 0;        /* border pixel of windows */
static const unsigned int gappx     = 15;        /* gaps between windows */
static const unsigned int snap      = 0;       /* snap pixel */
static const int showbar            = 1;        /* 0 means no bar */
static const int topbar             = 1;        /* 0 means bottom bar */
static const int vertpad            = 15;       /* vertical padding of bar */
static const int sidepad            = 15;       /* horizontal padding of bar */
static const char *fonts[]          = { "MesloLGS NF:style=Regular:pixelsize=10:antialias=true:autohint=true" };
static const char dmenufont[]       = "MesloLGS NF:style=Regular:pixelsize=10:antialias=true:autohint=true";
static const char col_norm[]        = "#b3b3b3";
static const char col_sel[]         = "#ffffff";
static const char col_bg[]          = "#101214";
static const char *colors[][3]      = {
        /*               fg        bg      border */
        [SchemeNorm] = { col_norm, col_bg, col_bg },
        [SchemeSel]  = { col_sel,  col_bg, col_bg },
        [SchemeStatus]={ col_sel,  col_bg, NULL   },
};
```

Statusbar
---------
Delimiter: ``` | ```
```
Time
Date
Volume
Eth-operstate
```

Commands
--------
```
static char dmenumon[2] = "0"; /* component of dmenucmd, manipulated in spawn() */
static const char *dmenucmd[]     = { "dmenu_run", "-c", "-l", "5", NULL };
static const char *applaunch[]    = { "/home/philip/.cargo/bin/yah", "a", NULL };
static const char *scrlaunch[]    = { "/home/philip/.cargo/bin/yah", "s", NULL };
static const char *termcmd[]      = { "st", NULL };
static const char *browser[]      = { "chromium", NULL };
static const char *incognitocmd[] = { "chromium", "-incognito", NULL };
static const char *lf[]           = { "st", "-e", "lf", NULL };
static const char *voldown[]      = { "pactl", "set-sink-volume", "@DEFAULT_SINK@", "-5%", NULL };
static const char *volup[]        = { "pactl", "set-sink-volume", "@DEFAULT_SINK@", "+5%", NULL };
static const char *editor[]       = { "st", "-e", "nvim", NULL };
static const char *spotify[]      = { "spotify", NULL };
static const char *passcmd[]      = { "passmenu", "-c", "-l", "5", NULL };
static const char *charpick[]     = { "/home/philip/.cargo/bin/yah", "c", NULL };
```

Keymap
------
```
/* modifier                     key            function        argument */
{ MODKEY,                       XK_space,      spawn,          {.v = applaunch } },
{ MODKEY|ShiftMask,             XK_space,      spawn,          {.v = scrlaunch } },
{ MODKEY,                       XK_Return,     zoom,           {0} },
{ MODKEY,                       XK_semicolon,  spawn,          {.v = termcmd } },
{ MODKEY,                       XK_d,          spawn,          {.v = browser } },
{ MODKEY|ShiftMask,             XK_d,          spawn,          {.v = incognitocmd } },
{ MODKEY,                       XK_f,          spawn,          {.v = lf } },
{ MODKEY,                       XK_c,          spawn,          {.v = voldown } },
{ MODKEY,                       XK_v,          spawn,          {.v = volup } },
{ MODKEY,                       XK_g,          spawn,          {.v = editor } },
{ MODKEY,                       XK_s,          spawn,          {.v = spotify } },
{ MODKEY,                       XK_apostrophe, spawn,          {.v = charpick } },
{ MODKEY,                       XK_a,          spawn,          {.v = passcmd } },
{ MODKEY,                       XK_r,          togglebar,      {0} },
{ MODKEY,                       XK_j,          focusstack,     {.i = +1 } },
{ MODKEY,                       XK_k,          focusstack,     {.i = -1 } },
{ MODKEY,                       XK_h,          setmfact,       {.f = -0.05} },
{ MODKEY,                       XK_l,          setmfact,       {.f = +0.05} },
{ MODKEY,                       XK_w,          killclient,     {0} },
{ MODKEY,                       XK_y,          setlayout,      {.v = &layouts[0]} },
{ MODKEY,                       XK_u,          setlayout,      {.v = &layouts[1]} },
{ MODKEY,                       XK_i,          setlayout,      {.v = &layouts[2]} },
{ MODKEY,                       XK_p,          togglefloating, {0} },
{ MODKEY,                       XK_0,          view,           {.ui = ~0 } },
{ MODKEY,                       XK_m,          focusmon,       {.i = -1 } },
{ MODKEY,                       XK_comma,      focusmon,       {.i = +1 } },
{ MODKEY|ShiftMask,             XK_m,          tagmon,         {.i = -1 } },
{ MODKEY|ShiftMask,             XK_comma,      tagmon,         {.i = +1 } },
```
