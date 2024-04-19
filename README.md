<a name="readme-top"></a>

# ryu - Real-time chat, voice, and community features in a modern, scalable Next.js 14-powered platform.

![ryu - Real-time chat, voice, and community features in a modern, scalable Next.js 14-powered platform.](/github/images/img_main.png "ryu - Real-time chat, voice, and community features in a modern, scalable Next.js 14-powered platform.")


<!-- Table of Contents -->
<details>

<summary>

# :notebook_with_decorative_cover: Table of Contents

</summary>

- [Folder Structure](#bangbang-folder-structure)
- [Getting Started](#toolbox-getting-started)
- [Screenshots](#camera-screenshots)
- [Tech Stack](#gear-tech-stack)
- [Stats](#wrench-stats)
- [Contribute](#raised_hands-contribute)
- [Acknowledgements](#gem-acknowledgements)
- [Learn More](#books-learn-more)
- [Deploy on Railway](#page_with_curl-deploy-on-railway)
- [Give A Star](#star-give-a-star)
- [Star History](#star2-star-history)
- [Give A Star](#star-give-a-star)

</details>

## :bangbang: Folder Structure

Here is the folder structure of this app.

```bash
discord-clone/
  |- actions/
    |- challenge-progress.ts
    |- user-progress.ts
    |- user-subscription.ts
  |- app/
    |-- (auth)/
        |--- (routes)/
            |---- account/
            |---- sign-in/
            |---- sign-up/
        |--- layout.tsx
    |-- (invite)/(routes)/invite/[inviteCode]/
    |-- (main)/
        |--- (routes)/servers/[serverId]/
            |---- channels/[channelId]/
            |---- conversations/[memberId]/
            |---- layout.tsx
            |---- page.tsx
        |--- layout.tsx
    |-- (setup)/
        |--- page.tsx
    |-- api/
        |--- channels/
        |--- direct-messages/
        |--- livekit/
        |--- members/
        |--- messages/
        |--- servers/
        |--- uploadthing/
    |-- apple-icon.png
    |-- error.tsx
    |-- favicon.ico
    |-- globals.css
    |-- icon1.png
    |-- icon2.png
    |-- layout.tsx
    |-- loading.tsx
    |-- not-found.tsx
  |- components/
    |-- chat/
    |-- clerk/
    |-- modals/
    |-- navigation/
    |-- providers/
    |-- server/
    |-- ui/
    |-- action-tooltip.tsx
    |-- emoji-picker.tsx
    |-- file-upload.tsx
    |-- media-room.tsx
    |-- mobile-toggle.tsx
    |-- mode-toggle.tsx
    |-- socket-indicator.tsx
    |-- user-avatar.tsx
  |- config/
    |-- index.ts
  |- hooks/
    |-- use-chat-query.ts
    |-- use-chat-scroll.ts
    |-- use-chat-socket.ts
    |-- use-modal-store.ts
    |-- use-origin.ts
  |- lib/
    |-- conversation.ts
    |-- current-profile-page.ts
    |-- current-profile.ts
    |-- db.ts
    |-- initial-profile.ts
    |-- uploadthing.ts
    |-- utils.ts
  |- pages/api/socket/
    |-- direct-messages/
    |-- messages/
    |-- io.ts
  |- prisma/
    |-- schema.prisma
  |- public/
    |-- github.png
    |-- logo.png
  |- .env
  |- .env.example
  |- .eslintrc.js
  |- .gitignore
  |- .prettierrc.json
  |- components.json
  |- constants.ts
  |- drizzle.config.ts
  |- environment.d.ts
  |- middleware.ts
  |- next.config.mjs
  |- package-lock.json
  |- package.json
  |- postcss.config.js
  |- tailwind.config.ts
  |- tsconfig.json
```

<br />

## :toolbox: Getting Started

1. Make sure **Git** and **NodeJS** is installed.
2. Clone this repository to your local computer.
3. Create `.env` file in **root** directory.
4. Contents of `.env`:

```env
# .env

# disabled next.js telemetry
NEXT_TELEMETRY_DISABLED=1

# clerk auth keys
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_test_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
CLERK_SECRET_KEY=sk_test_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

# clerk redirect urls
NEXT_PUBLIC_CLERK_SIGN_IN_URL=/sign-in
NEXT_PUBLIC_CLERK_SIGN_UP_URL=/sign-up
NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL=/
NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL=/

# neon databse url
DATABASE_URL="postgresql://<user>:<password>@<host>:<post>/discord-clone?sslmode=require"

# uploading api key and app id
UPLOADTHING_SECRET=sk_live_XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
UPLOADTHING_APP_ID=xxxxxxxxxxxxx

# app base url
NEXT_PUBLIC_BASE_URL=http://localhost:3000

# livekit api keys and public url
LIVEKIT_API_KEY=XXXXXXXXXXXXXXXXX
LIVEKIT_API_SECRET=XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
NEXT_PUBLIC_LIVEKIT_URL=wss://discord-clone-xxxxxxxxxx.livekit.cloud

```

5. **Next.js Telemetry Disabled:**

   - Visit the Next.js documentation or repository.
   - Find the instructions to disable telemetry.
   - Set `NEXT_TELEMETRY_DISABLED` to `1` in your `.env` file.

6. **Clerk Authentication Keys:**

   - Go to the Clerk website and sign in to your account.
   - Navigate to the settings or API keys section.
   - Generate or locate your Clerk publishable and secret keys.
   - Set `NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY` and `CLERK_SECRET_KEY` accordingly in the `.env` file.

7. **Clerk Redirect URLs:**

   - Refer to the Clerk documentation or settings.
   - Set the required URLs for sign-in, sign-up, after sign-in, and after sign-up.
   - Assign these URLs to `NEXT_PUBLIC_CLERK_SIGN_IN_URL`, `NEXT_PUBLIC_CLERK_SIGN_UP_URL`, `NEXT_PUBLIC_CLERK_AFTER_SIGN_IN_URL`, and `NEXT_PUBLIC_CLERK_AFTER_SIGN_UP_URL` respectively in the `.env` file.

8. **Neon Database URL:**

   - Access your database provider (e.g., PostgreSQL).
   - Retrieve the necessary connection details such as username, password, host, and port.
   - Construct the database URL using the obtained information and SSL mode.
   - Assign the constructed URL to `DATABASE_URL` in the `.env` file.

9. **Uploading API Key and App ID:**

   - Go to the UploadThing website or application.
   - Find the section for API keys or account settings.
   - Generate or locate your secret key and app ID.
   - Set `UPLOADTHING_SECRET` and `UPLOADTHING_APP_ID` in the `.env` file accordingly.

10. **App Base URL:**

- Determine the base URL of your application.
- Set `NEXT_PUBLIC_BASE_URL` to the base URL in the `.env` file.

11. **Livekit API Keys and Public URL:**

- Visit the Livekit website or dashboard.
- Navigate to API settings or keys section.
- Generate or locate your API key and secret.
- Set `LIVEKIT_API_KEY`, `LIVEKIT_API_SECRET`, and `NEXT_PUBLIC_LIVEKIT_URL` in the `.env` file according to the obtained information.

12. Save and Secure:

    - Save the changes to the `.env.local` file.

13. Install Project Dependencies using `npm install --legacy-peer-deps` or `yarn install --legacy-peer-deps`.

14. Now app is fully configured 👍 and you can start using this app using either one of `npm run dev` or `yarn dev`.

**NOTE:** Please make sure to keep your API keys and configuration values secure and do not expose them publicly.

## :camera: Screenshots

![Modern UI/UX](/github/images/img1.png "Modern UI/UX")

![Video Conferencing](/github/images/img2.png "Video Conferencing")

![One-on-one Chat](/github/images/img3.png "One-on-one Chat")

## :gear: Tech Stack

[![React JS](https://skillicons.dev/icons?i=react "React JS")](https://react.dev/ "React JS") [![Next JS](https://skillicons.dev/icons?i=next "Next JS")](https://nextjs.org/ "Next JS") [![Typescript](https://skillicons.dev/icons?i=ts "Typescript")](https://www.typescriptlang.org/ "Typescript") [![Tailwind CSS](https://skillicons.dev/icons?i=tailwind "Tailwind CSS")](https://tailwindcss.com/ "Tailwind CSS") [![Vercel](https://skillicons.dev/icons?i=vercel "Vercel")](https://vercel.app/ "Vercel") [![Postgresql](https://skillicons.dev/icons?i=postgres "Postgresql")](https://www.postgresql.org/ "Postgresql")

## :wrench: Stats

[![Stats for ryu](/.github/images/stats.svg "Stats for ryu")](https://pagespeed.web.dev/analysis?url=https://discord-clone-production-e781.up.railway.app/ "Stats for ryu")

## :raised_hands: Contribute

You might encounter some bugs while using this app. You are more than welcome to contribute. Just submit changes via pull request and I will review them before merging. Make sure you follow community guidelines.

## :gem: Acknowledgements

Useful resources and dependencies that are used in ryu.

- [@clerk/nextjs](https://www.npmjs.com/package/@clerk/nextjs): ^4.29.9
- [@clerk/themes](https://www.npmjs.com/package/@clerk/themes): ^1.7.10
- [@emoji-mart/data](https://www.npmjs.com/package/@emoji-mart/data): ^1.1.2
- [@emoji-mart/react](https://www.npmjs.com/package/@emoji-mart/react): ^1.1.1
- [@hookform/resolvers](https://www.npmjs.com/package/@hookform/resolvers): ^3.3.4
- [@livekit/components-react](https://www.npmjs.com/package/@livekit/components-react): ^2.0.5
- [@livekit/components-styles](https://www.npmjs.com/package/@livekit/components-styles): ^1.0.11
- [@prisma/client](https://www.npmjs.com/package/@prisma/client): ^5.11.0
- [@radix-ui/react-avatar](https://www.npmjs.com/package/@radix-ui/react-avatar): ^1.0.4
- [@radix-ui/react-dialog](https://www.npmjs.com/package/@radix-ui/react-dialog): ^1.0.5
- [@radix-ui/react-dropdown-menu](https://www.npmjs.com/package/@radix-ui/react-dropdown-menu): ^2.0.6
- [@radix-ui/react-label](https://www.npmjs.com/package/@radix-ui/react-label): ^2.0.2
- [@radix-ui/react-popover](https://www.npmjs.com/package/@radix-ui/react-popover): ^1.0.7
- [@radix-ui/react-scroll-area](https://www.npmjs.com/package/@radix-ui/react-scroll-area): ^1.0.5
- [@radix-ui/react-select](https://www.npmjs.com/package/@radix-ui/react-select): ^2.0.0
- [@radix-ui/react-separator](https://www.npmjs.com/package/@radix-ui/react-separator): ^1.0.3
- [@radix-ui/react-slot](https://www.npmjs.com/package/@radix-ui/react-slot): ^1.0.2
- [@radix-ui/react-tooltip](https://www.npmjs.com/package/@radix-ui/react-tooltip): ^1.0.7
- [@tanstack/react-query](https://www.npmjs.com/package/@tanstack/react-query): ^4.35.3
- [@uploadthing/react](https://www.npmjs.com/package/@uploadthing/react): ^6.4.1
- [axios](https://www.npmjs.com/package/axios): ^1.6.8
- [class-variance-authority](https://www.npmjs.com/package/class-variance-authority): ^0.7.0
- [clsx](https://www.npmjs.com/package/clsx): ^2.1.0
- [cmdk](https://www.npmjs.com/package/cmdk): ^1.0.0
- [date-fns](https://www.npmjs.com/package/date-fns): ^3.6.0
- [emoji-mart](https://www.npmjs.com/package/emoji-mart): ^5.5.2
- [livekit-server-sdk](https://www.npmjs.com/package/livekit-server-sdk): ^2.1.2
- [lucide-react](https://www.npmjs.com/package/lucide-react): ^0.363.0
- [next](https://www.npmjs.com/package/next): 14.1.4
- [next-themes](https://www.npmjs.com/package/next-themes): ^0.3.0
- [query-string](https://www.npmjs.com/package/query-string): ^9.0.0
- [react](https://www.npmjs.com/package/react): ^18
- [react-dom](https://www.npmjs.com/package/react-dom): ^18
- [react-hook-form](https://www.npmjs.com/package/react-hook-form): ^7.51.1
- [socket.io](https://www.npmjs.com/package/socket.io): ^4.7.5
- [socket.io-client](https://www.npmjs.com/package/socket.io-client): ^4.7.5
- [tailwind-merge](https://www.npmjs.com/package/tailwind-merge): ^2.2.2
- [tailwindcss-animate](https://www.npmjs.com/package/tailwindcss-animate): ^1.0.7
- [uploadthing](https://www.npmjs.com/package/uploadthing): ^6.7.0
- [uuid](https://www.npmjs.com/package/uuid): ^9.0.1
- [zod](https://www.npmjs.com/package/zod): ^3.22.4
- [zustand](https://www.npmjs.com/package/zustand): ^4.5.2
- [@types/node](https://www.npmjs.com/package/@types/node): ^20
- [@types/react](https://www.npmjs.com/package/@types/react): ^18
- [@types/react-dom](https://www.npmjs.com/package/@types/react-dom): ^18
- [@types/uuid](https://www.npmjs.com/package/@types/uuid): ^9.0.8
- [autoprefixer](https://www.npmjs.com/package/autoprefixer): ^10.0.1
- [eslint](https://www.npmjs.com/package/eslint): ^8
- [eslint-config-next](https://www.npmjs.com/package/eslint-config-next): 14.1.4
- [postcss](https://www.npmjs.com/package/postcss): ^8
- [prisma](https://www.npmjs.com/package/prisma): ^5.11.0
- [tailwindcss](https://www.npmjs.com/package/tailwindcss): ^3.3.0
- [typescript](https://www.npmjs.com/package/typescript): ^5

## :coffee: Buy Me a Coffee

[<img src="https://img.shields.io/badge/Buy_Me_A_Coffee-FFDD00?style=for-the-badge&logo=buy-me-a-coffee&logoColor=black" width="200" />](https://www.buymeacoffee.com/sanidhy "Buy me a Coffee")

## :rocket: Follow Me

[![Follow Me](https://img.shields.io/github/followers/sanidhyy?style=social&label=Follow&maxAge=2592000)](https://github.com/sanidhyy "Follow Me")
[![Tweet about this project](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Ftwitter.com%2FTechnicalShubam)](https://twitter.com/intent/tweet?text=Check+out+this+amazing+app:&url=https%3A%2F%2Fgithub.com%2Fsanidhyy%2Fdiscord-clone "Tweet about this project")
[![Subscribe to my YouTube Channel](https://img.shields.io/youtube/channel/subscribers/UCNAz_hUVBG2ZUN8TVm0bmYw)](https://www.youtube.com/@OPGAMER./?sub_confirmation=1 "Subscribe to my YouTube Channel")

## :books: Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js/) - your feedback and contributions are welcome!

## :page_with_curl: Deploy on Railway

Deploying your Next.js app on Railway.app is simple and straightforward.

1. **Sign up or Log in:**

   - Head over to [Railway.app](https://railway.app/) and either sign up for a new account or log in to your existing one.

2. **Connect Repository:**

   - Connect your project repository (e.g., GitHub, GitLab, Bitbucket) to Railway.

3. **Configure Environment Variables:**

   - Set up your environment variables in Railway's dashboard or using their CLI. Ensure you include all required variables as per your project's configuration.

4. **Set Up Build Command:**

   - Configure your build command to ensure Railway can build and deploy your Next.js app correctly. Typically, this command will be `yarn build` or `npm run build`.

5. **Deploy:**

   - Trigger the deployment process either from Railway's dashboard or through their CLI.

6. **Monitor Deployment:**

   - Once deployed, monitor the deployment process and check for any errors or warnings in Railway's dashboard.

7. **Custom Domain (Optional):**
   - If you have a custom domain, you can set it up with Railway to point to your deployed Next.js app.

For more detailed instructions or troubleshooting, refer to [Railway documentation](https://docs.railway.app/).

## :star: Give A Star

You can also give this repository a star to show more people and they can use this repository.

## :star2: Star History

<a href="https://star-history.com/#smxhmxd/ryu&Timeline">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=smxhmxd/ryu&type=Timeline&theme=dark" />
  <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=smxhmxd/ryu&type=Timeline" />
  <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=smxhmxd/ryu&type=Timeline" />
</picture>
</a>

<br />
<p align="right">(<a href="#readme-top">back to top</a>)</p>
