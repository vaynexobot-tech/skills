---
name: claude-code-tools-setup
description: Claude Code uchun 5 ta vositani (claude-mem, Superpowers, Impeccable, find-skills, Task Observer) barcha loyihalarda ishlaydigan qilib global o'rnatish va tekshirish. Foydalanuvchi shu vositalarni o'rnatish, qayta o'rnatish yoki tekshirishni so'raganda ishlat.
---

# Claude Code vositalarini global o'rnatish

Har bir vosita muallifning README faylidagi Claude Code usuli bilan o'rnatiladi. Javoblar o'zbek tilida, qisqa.

## 1. Terminalda (oddiy shell)

```
npx skills add vercel-labs/skills --skill find-skills -a claude-code -g
npx skills add rebelytics/one-skill-to-rule-them-all --skill task-observer -a claude-code -g
npx impeccable install --providers=claude --scope=global
```

- Impeccable o'rnatuvchisi dizayn hookini taklif qilsa, qabul qil. Flaglar xato bersa, `npx impeccable install` ni ishga tushirib, menyudan Claude Code va Global ni tanla.
- Task Observer `references/` va `scripts/` papkalari bilan to'liq o'rnatilganini tekshir: `ls ~/.claude/skills/task-observer`.

## 2. Claude Code ichida

```
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
/plugin install superpowers@claude-plugins-official
```

So'ng Claude Code'ni qayta ishga tushir. Plaginlar foydalanuvchi darajasida o'rnatiladi, ya'ni barcha loyihalarda ishlaydi.

## 3. claude-mem xizmatini tekshirish

- `npx claude-mem doctor`: Bun, uv, hook va worker holatini tekshiradi.
- Port `~/.claude-mem/settings.json` da. Brauzerda `http://localhost:<port>/viewer` ochiladi.
- Node.js 20.19+ yoki 22.12+ kerak.

## 4. Task Observer faollashtirish bloki

Blok `~/.claude/skills/task-observer/references/environments.md` faylidagi "The activation block" qismida.

1. O'sha blokni o'qi.
2. `~/.claude/CLAUDE.md` da shu blok borligini tekshir (masalan, blokning birinchi qatori bo'yicha `grep`).
3. Yo'q bo'lsa, mavjud matnga tegmasdan fayl oxiriga qo'sh. Bor bo'lsa, ikkinchi nusxa qo'shma.
4. `[ABSOLUTE PATH]` va `[PROJECTS ROOT]` uchun yo'llarni foydalanuvchidan so'ra.

## 5. Ishlatish misollari

- **claude-mem**: yangi sessiyada oldingi kontekst o'zi chiqadi.
- **Superpowers**: "Let's make a react todo list" deb yoz. Claude kod yozishdan oldin brainstorming savollarini berishi kerak.
- **Impeccable**: loyihada bir marta `/impeccable init`, keyin `/impeccable polish settings`.
- **find-skills**: "Telegram bot uchun skill bormi?" deb so'ra.
- **Task Observer**: sessiya oxirida "Any observations logged?" deb so'ra. Bir necha sessiyadan keyin `skill-observations/observation-log/` paydo bo'lmasa, faollashtirish ishlamagan.

## Manbalar

- https://github.com/thedotmack/claude-mem
- https://github.com/obra/superpowers
- https://github.com/pbakaus/impeccable
- https://github.com/vercel-labs/skills
- https://github.com/rebelytics/one-skill-to-rule-them-all
