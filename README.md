# zt0ne's edited version of Luke's build of st - the simple (suckless) terminal

The [suckless terminal (st)](https://st.suckless.org/) with some additional features:

+ Compatibility with `Xresources` and `pywal` for dynamic colors.
+ Default solarized colors otherwize.
+ Transparency/alpha, which is also adjustable from `~/.Xresources`.
+ Default font is system "mono" at 14pt, meaning the font will match your system font.
+ Very useful keybinds including:
	+ Copy is alt-c, paste is alt-v or alt-p pastes from primary selection
	+ Zoom in/out or increase font size with Alt+Shift+k/j or u/d for larger intervals.
	+ Hold alt and press either ↑/↓ or the vim keys k/j to move up/down in the terminal.
	+ Shift+Mouse wheel do the same.
	+ Alt-u and Alt-d scroll back/forward in history a page at a time.
	+ Alt-PageUp and Alt-PageDown will do the same.
+ Vertcenter
+ Scrollback
+ updated to latest version 0.8.1

The following additional bindings were added before I forked this:

+ Scroll through history -- Shift+PageUp/PageDown or Shift+Mouse wheel
+ Increase/decrease font size -- Shift+Alt+PageUp/PageDown
+ Return to default font size -- Shift+Alt+Home
+ Paste -- Shift+Insert

## Installation for newbs

```
make
sudo make install
```

Obviously, `make` is required to build. `fontconfig` is required for the
default build, since it asks `fontconfig` for your system monospace font.  It
might be obvious, but `libX11` and `libXft` are required as well. Chances are,
you have all of this installed already.

## How to configure dynamically with Xresrouces

For many key variables, this build of `st` will look for X settings set in
either `~/.Xdefaults` or `~/.Xresources`. You must run `xrdb` on one of these
files to load the settings.

For example, you can define your desired fonts, transparency or colors:

```
*.font:	Liberation Mono:pixelsize=12:antialias=true:autohint=true;
*.alpha: 150
*.color0: #111
...
```

The `alpha` value (for transparency) goes from `0` (transparent) to `255`
(opaque).

### Colors

To be clear about the color settings:

- This build will use colorized colors by default and as a fallback.
- If there are Xresources colors defined, those will take priority.
- But if `wal` has run in your session, its colors will take priority.

Note that when you run `wal`, it will negate the transparency of existing
windows, but new windows will continue with the previously defined
transparency.

## Contact

- Luke Smith <luke@lukesmith.xyz>
- [https://lukesmith.xyz](https://lukesmith.xyz)
