# 🚀 Git Tip: Keep Your History Clean with `git pull --rebase`

### 📝 TL;DR Command Summary

| Goal | Command |
| --- | --- |
| **Pull with Rebase** | `git pull --rebase` |
| **Abort Rebase** | `git rebase --abort` |
| **Continue after fixing conflicts** | `git rebase --continue` |
| **Create Shortcut** | `git config --global alias.pr 'pull --rebase'` |

---

### ❌ The Problem: The "Useless" Merge Commit

When you and a teammate (e.g., "John") work on the same branch and John pushes his changes first, your subsequent `git push` will be rejected because the remote branch is ahead of your local one.

If you run a standard `git pull`, Git creates a **merge commit**.

* **The Downside:** This "useless" commit clutters your project history, making it non-linear and difficult to navigate when trying to locate specific features or bug fixes later.

---

### ✅ The Solution: `git pull --rebase`

Instead of merging, use the rebase flag.

```bash
git pull --rebase

```

**How it works:**

1. It temporarily sets your local (unpushed) commits aside.
2. It pulls down the remote changes from your teammate.
3. It **reapplies** your local commits on top of the new remote changes.

**The Benefit:**

> 💎 **Result:** A perfectly linear, clean history that looks as if you wrote your code *after* your teammate finished theirs.

---

### 🛡️ Safety First: The "Undo" Button

Rebasing can sometimes lead to complex conflicts. If you feel stuck or unsure during the process, you have a safe exit.

If the conflict is too messy, simply run:

```bash
git rebase --abort

```

This instantly restores your repository to its state **before** you started the pull, allowing you to try again or switch to a standard merge.

---

### ⚡ Pro Tip: Save Time with an Alias

Typing `--rebase` every time can be tedious. You can create a global alias (e.g., `git pr`) to speed up your workflow.

**To set up the alias:**

```bash
git config --global alias.pr 'pull --rebase'

```

*Now you can just type `git pr`!*

---

### Source

[1. Philomatics - Youtube](https://www.youtube.com/watch?v=xN1-2p06Urc)
