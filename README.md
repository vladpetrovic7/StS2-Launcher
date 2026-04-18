# StS2 Launcher — unofficial font-fix build

This is an **unofficial fork** of [Ekyso/StS2-Launcher](https://github.com/Ekyso/StS2-Launcher) with a small patch that fixes the post-update black screen on Android.

If you were using Ekyso's launcher and it started black-screening after the recent Slay the Spire 2 update, this build should get you playing again.

A pull request with the fix is open upstream ([Ekyso/StS2-Launcher#49](https://github.com/Ekyso/StS2-Launcher/pull/49)). Once it's merged and Ekyso cuts a new release, you can go back to the official build.

---

## Download

Latest APK: **[Releases page](https://github.com/vladpetrovic7/StS2-Launcher/releases/latest)** → download the `.apk` asset.

## Install

You need:

- An Android phone (tested on Samsung — other vendors probably work but unconfirmed).
- A Steam account that owns **Slay the Spire 2**. The APK does not contain any game files; it downloads them from your Steam account on first run.

Steps:

1. **If you already have Ekyso's launcher installed: uninstall it first.** Android won't install this one over it because it's signed with a different key. Uninstalling wipes the local data; in-game progress is saved to Steam Cloud, but any unsaved run state is lost.
2. Download the APK from the Releases page to your phone (or to your PC and sideload).
3. Open it. Android will warn about "install from unknown sources" — allow it for whichever app you're installing from (browser, file manager, etc.).
4. Open the app, log in with Steam, wait for the game to re-download, and play.

## What's different from Ekyso's version

Just one patch, plus a build fix:

- **Font-substitution crash workaround.** The updated game throws a `NullReferenceException` inside `FontControlUtils.ApplyLocaleFontSubstitution` when any UI label initialises on mobile. Left alone, this kills the entire UI and you see a black screen. This build swallows that exception so labels fall back to the theme default font. Looks fine in English; other languages might look less polished until MegaCrit ships a real fix.
- **Reflection-based mod loader.** The game renamed some internal fields (`Mod.wasLoaded` etc.) in the update, which broke one of Ekyso's existing patches. This build looks those fields up by reflection so they keep working.

Full diff: [PR #49](https://github.com/Ekyso/StS2-Launcher/pull/49).

## Heads-up

- This APK is signed with a **locally-generated debug keystore**, not a real release key. It's fine for sideloading but Google Play would reject it, and you can't install it over the official build (or vice versa) without uninstalling first.
- I'm not planning to keep this fork maintained long-term. Once the upstream PR is merged, use Ekyso's build.

## Credits

All real work on this launcher is by **[Ekyso](https://github.com/Ekyso)** and contributors. See the [upstream repo](https://github.com/Ekyso/StS2-Launcher) and the original developer README preserved here as [UPSTREAM-README.md](UPSTREAM-README.md).

## License

MIT, same as upstream. See [LICENSE](LICENSE).
