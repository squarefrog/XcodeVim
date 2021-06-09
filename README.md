# Vim key bindings in Xcode 13

New in Xcode 13 is the inclusion of Vim key bindings.

Using Vim key bindings when writing code can have huge benefits to your efficiency, but it does have a fairly steep learning curve.

I'd like to show you some of the basic features to get you up to speed.

## First steps

Firstly, lets enable the key bindings. In Xcode 13, open up the Preferences and go to Text Editing > Editing > ✅ Vim key bindings.

![Xcode Text Editing Settings](https://github.com/squarefrog/XcodeVim/raw/main/images/Settings.png)

## Modes

To start with, it's important to know that there are 3 different modes for Vim key bindings:

### Normal Mode <kbd>esc</kbd>

You'd primarily use this mode for moving around your file and performing tasks like yank, paste, delete etc. As the name suggests, this should be your normal mode of operation.

### Insert Mode <kbd>i</kbd>

Insert mode is the mode you're already familiar with - it allows you to enter text freely. To leave Insert mode, and return to Normal mode, press the escape key.

### Visual Mode <kbd>v</kbd>

Visual mode allows you to select specific text quickly to later yank to the pasteboard.

## Switching modes

While you're flying round your code in Normal mode, you may want to jump into Insert mode to make a quick change. You can always press <kbd>i</kbd> to jump into Insert mode, but there are other options too:

<kbd>o</kbd>: insert a new line below the current line, and enter Insert mode
<kbd>O</kbd>: insert a new line above the current line, and enter Insert mode
<kbd>c</kbd>: change - must be accompanied with a motion command

<kbd>c</kbd> really is where things get interesting. Suppose you have the following declaration:

```swift
var age = 42
```

The compiler helpfully tells you that it's safe to convert this to a `let` property. You _could_ use the quick fix-it, but you're more adventurous than that! Positioning the cursor on the letter `v`, type <kbd>cw</kbd> (change word). That deletes the whole word and drops you into insert mode to carry on typing `let`. More on the <kbd>w</kbd> command later on.

## Basic Navigation

As Vim key bindings are a layer above normal Xcode function, you can skip 'traditional' movement keys. Seasoned Vim veterans will not like that, but here's a guide just in case:

<kbd>h</kbd> move left one character
<kbd>j</kbd> move down one character
<kbd>k</kbd> move up one character
<kbd>l</kbd> move right one character

Alternatively, you can just use the traditional arrow keys. However, moving one character at a time isn't terribly efficient. Thankfully, Vim has _many_ ways to improve your efficiency. The first of which is the repeat command.

Lets say you'd like to move your cursor 5 characters to the right. You could tap <kbd>l</kbd> five times, but a better way is to type <kbd>5l</kbd>. Give that a try in Xcode now. I'll wait.

The repeat command works with most commands, which I'll remind you about later.

## Intermediate navigation

Moving characterwise is fine, but you're probably thinking 'well I can do that now, what's the point?'. And you'd be right. Thankfully there are much better ways of navigating. Here's a summary:

<kbd>b</kbd>: move to the beginning of the previous word
<kbd>w</kbd>: move to the beginning of the next word
<kbd>e</kbd>: move to the end of the word
<kbd>0</kbd>: move to the absolute start of the line
<kbd>$</kbd>: move to the end of the line
<kbd>^</kbd>: move to the first character of the line, ignore whitespace.
<kbd>-</kbd>: move to the first character of the previous line, ignoring whitespace.

Of course you can also combine these with repeat. So to move 4 words along, type <kbd>4w</kbd>.

Now lets try jumping to characters even quicker with the following:

<kbd>f</kbd>: find next occurrence of a character. For example <kbd>fp</kbd> will find the next `p` character.
<kbd>%</kbd>: jump to next matching delimiter, i.e. the matching brace, or quote mark etc.

Suppose you have a function, and you want to jump to the opening brace. You would simply type <kbd>f{</kbd>. To get to the closing brace, when your cursor is over the opening brace, type <kbd>%</kbd>.

## Clipboard operation

In Normal mode you can quickly copy and paste things using yank (copy) and paste.

<kbd>y</kbd>: yank the selection to the clipboard
<kbd>p</kbd>: paste from the clipboard
<kbd>d</kbd>: delete a selection, copying it into the clipboard - similar to the Cut action

Yank supports motion, so to copy an entire line, press <kbd>yy</kbd>. To paste below the current line, press <kbd>p</kbd>. To paste above the current line, press <kbd>P</kbd>.

You can also combine yank with the navigation commands listed above. For example, to yank up to the beginning of the next word, <kbd>yw</kbd>. To yank to the end of the line, <kbd>y$</kbd>.

Similarly, you can cut text using <kbd>d</kbd>. For example, to delete a word, with your cursor on the word, type <kbd>dw</kbd>. To delete an entire line, <kbd>dd</kbd>.

## More information

The advantage of Vim being almost 30 years old, is there are a wealth of great resources for learning Vim.

One of my absolute favourites for beginners is [Vim Adventures](https://vim-adventures.com), where you can learn basic Vim navigation by playing a game!

[Derek Wyatt](http://derekwyatt.org/vim/tutorials/index.html) has a superb set of videos at beginner, intermediate and advanced levels.

## Improvements?

If you'd like to expand or improve this guide, [Pull Requests](https://github.com/squarefrog/XcodeVim/pulls) are open!
