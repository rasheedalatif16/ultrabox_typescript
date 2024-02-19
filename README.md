# UltraBox

pandinboxis an online tool for sketching and sharing instrumental music.
You can find it [here](https://pandinboxing.github.io).
It is a modification of Goldbox, which itself is a modification of JummBox, which inturn is a modification of the [original BeepBox](https://beepbox.co).

The goal of UltraBox is to combine every single beepbox mod into one. Feel free to contribute!


All song data is packaged into the URL at the top of your browser. When you make
changes to the song, the URL is updated to reflect your changes. When you are
satisfied with your song, just copy and paste the URL to save and share your
song!

UltraBox, as well as GoldBox, Jummbox, and Beepbox which it's based on, are free projects. If you ever feel so inclined, please support the original creator, [John Nesky](http://www.johnnesky.com/), via
[PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_donations&business=QZJTX9GRYEV9N&currency_code=USD)!
JummBox is developed by [Jummbus](http://www.twitter.com/jummbus).

## Compiling

The compilation procedure is identical to the repository for BeepBox. I will include the excerpt on compiling from that page's readme below for convenience:

The source code is available under the MIT license. The code is written in
[TypeScript](https://www.typescriptlang.org/), which requires
[node & npm](https://www.npmjs.com/get-npm), so install those first. Then to
build this project, open a command line ([Git Bash](https://gitforwindows.org/)) and run:

```
git clone https://github.com/ultraabox/ultrabox_typescript
cd ultrabox_typescript
npm install
npm run build
```

JummBox (and by extension, Ultrabox) makes a divergence from BeepBox that necessitates an additional dependency:
rather than using the (rather poor) default HTML select implementation, the custom
library [select2](https://select2.org) is employed. select2 has an explicit dependency
on [jQuery](https://jquery.com) as well, so you may need to install the following
additional dependencies if they are not picked up automatically.

```
npm install select2
npm install @types/select2
npm install @types/jquery
```

## Code

The code is divided into several folders. This architecture is identical to BeepBox's.

The [synth/](synth) folder has just the code you need to be able to play UltraBox
songs out loud, and you could use this code in your own projects, like a web
game. After compiling the synth code, open website/synth_example.html to see a
demo using it. To rebuild just the synth code, run:

```
npm run build-synth
```

The [editor/](editor) folder has additional code to display the online song
editor interface. After compiling the editor code, open website/index.html to
see the editor interface. To rebuild just the editor code, run:

```
npm run build-editor
```

The [player/](player) folder has a miniature song player interface for embedding
on other sites. To rebuild just the player code, run:

```
npm run build-player
```

The [website/](website) folder contains index.html files to view the interfaces.
The build process outputs JavaScript files into this folder.


Finally, the [app/](app) folder contains several files for the offline version of UltraBox. Building the app version outputs JavaScript files into this folder.
The [app_editor/](app_editor) folder contains a seperate version of the [editor/](editor) files specific to the offline version.

## Dependencies

Most of the dependencies are listed in [package.json](package.json), although
I'd like to note that UltraBox also has an indirect, optional dependency on
[lamejs](https://www.npmjs.com/package/lamejs) via
[jsdelivr](https://www.jsdelivr.com/) for exporting .mp3 files. If the user
attempts to export an .mp3 file, JummBox will direct the browser to download
that dependency on demand.

## App Version

### Run without packaging (for debugging)
If you'd like to run the app version without packaging, run the following:
```
npm install
npm run build-app
npm run build-player
cd app
npm install electron
```

You'll need to manually move some extra files from the [website/](website) folder into the [app/](app) folder (such as the player files and the hotdog). To start the program, run:
```
npm run start
```

### Packaging (for distribution)
In order to package the program, first run the commands in the "Run without packaging" section, and then run the following:
```
npm install electron-packager
npm run package
```

Alternatively you can run ```npm run package-host``` if you'd like to package for only your host platform.

In order to package for Mac on a platform other than Mac, you'll have to run Git Bash as an administrator. 
