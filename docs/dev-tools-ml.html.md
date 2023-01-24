---
bibliography:
- src/ml.bib
csl: ./csls/chicago-fullnote-bibliography.csl
suppress-bibliography: true
title: Developer Tools for Machine Learning (ML)
---

Will innovative advances in artificial intelligence (AI) be restricted
to well-funded startups and big tech companies, or will we develop new
AI systems more collaboratively, following the model of open source
software? This question has practical and moral implications, like if
you'll have to pay for virtual language/research assistants, or if you
trust private companies to handle AI safety (alignment), content
moderation, and non-discrimination without input from academia or the
public sector.

The answer to this question lies in the ecosystem of developer tools for
machine learning, the programs that allow software engineers to re-use
published models, datasets, and weights, and combine them in interesting
new ways. While recent advances in private large language models have
spurred the creation of open ML research collectives,[^1] their models
are currently not competitive in quality with proprietary systems like
OpenAI ChatGPT. That goal will require significant effort on tools and
infrastructure, along with research into the promising but unknown
capabilities of federated and modular machine learning.[^2]

In this article, I will lay out the existing state of such ML tools in
four critical subtopics: model code, datasets, weights, and AutoML
tools. I hope to investigate the research question: What are key
challenges and opportunities that would enable faster, more
collaborative AI development?

For model code, most ML projects use industry-standard machine learning
frameworks or libraries, which implement key foundational math
operations like matrix multiplication and convolution, along with
algorithms like deep neural networks, recurrent networks, and many
others. These libraries offer functions to build more complex models out
of smaller building blocks, while compiling to highly optimized machine
code that can run on hardware accelerators like GPUs, or even custom
chips.[^3] The most popular frameworks are PyTorch, used by most
researchers and focused on Python, and Tensorflow, which has better
interfaces in other languages and more tools for deploying models.[^4]
These frameworks have been somewhat commoditized, with a project called
ONNX allowing developers to write a model in one framework and run
inference in another framework. There is a library called Keras which
offers an even simpler and more high level interface to the major
frameworks. However, to modify an existing model, developers still need
access to the original code and the knowledge of the framework it is
written in.

Most frameworks have built tools to make datasets easier to use. Sci-kit
learn and Torch each have a few toy datasets that can be loaded with a
single line of code, while Tensorflow has its own Dataset format with
thousands of standard datasets for many academic ML tasks.[^5] Usually a
certain ML task will have a primary dataset and benchmark that most
authors will use to evaluate and compare their contributions, with some
sites aggregating state of the art results.[^6] Often other datasets for
the same task will follow the format of this standard. Sometimes there
are many competing formats however without good tools to translate
between them, making it very difficult to properly process them for
machine learning.

Many authors have focused on taking existing (pre-trained) models and
fine-tuning them (e.g. keeping most weights but re-training the last few
layers) on specialized tasks and datasets. This relies on the original
model authors to publish their model weights --- the "learned" values or
connections for a trained instance of a model. HuggingFace is a new
platform that allows users to upload model weights, download and run
inference using pre-trained models with a few lines of code. They also
aim to allow fine-tuning although the experience is not as polished.
According to VentureBeat they "aim\[\] to become the GitHub of machine
learning," enabling developers to collaborate using over "100,000
pre-trained models and 10,000 datasets."[^7]

Finally, another interesting development is the rise of AutoML, where a
larger learning system searches for the optimal architecture or
hyperparameters for a neural network. There are several tools which make
these technologies easy to use, including MLJar which automatically
tests and compares many different ML methods including traditional
statistical ones like support vector machines, clustering, boosted
decision trees, and others by an accuracy metric,[^8] and Ludwig, which
focuses more on deep neural network approaches using an encoder/decoder
approach.[^9] These tools radically speed up model development, MLJar
offers simpler solutions first, like traditional machine learning rather
than deep learning models, which often perform better on certain
datasets. This can save developers from endless hours of tweaking and
over-engineering. Making these tools accessible for non-technical people
is probably the best short-term step towards democratizing machine
learning.

[^1]: Kyle Wiggers, "BigScience's AI Language Model Is Finally
    Available. TechCrunch," July 12, 2022,
    <https://techcrunch.com/2022/07/12/a-year-in-the-making-bigsciences-ai-language-model-is-finally-available/>.

[^2]: Colin Raffel, "A Call to Build Models Like We Build Open-Source
    Software," December 8, 2021,
    <https://colinraffel.com/blog/a-call-to-build-models-like-we-build-open-source-software.html>.

[^3]: "AI Chip List," accessed January 20, 2023,
    <https://github.com/basicmi/AI-Chip>.

[^4]: Ari Joury, "Why TensorFlow for Python Is Dying a Slow Death. TNW
    `\textbar`{=latex} House-of-Talent," January 13, 2023,
    <https://thenextweb.com/news/why-tensorflow-for-python-is-dying-a-slow-death>.

[^5]: "TensorFlow Datasets. TensorFlow," accessed January 20, 2023,
    <https://www.tensorflow.org/datasets/catalog/overview>.

[^6]: "Papers with Code - Browse the State-of-the-Art in Machine
    Learning," accessed January 23, 2023,
    <https://paperswithcode.com/sota>.

[^7]: "Hugging Face Takes Step Toward Democratizing AI and ML.
    VentureBeat," September 27, 2022,
    <https://venturebeat.com/ai/hugging-face-steps-toward-democratizing-ai-and-ml-with-latest-offering￼/>.

[^8]: "MLJAR Automated Machine Learning for Humans" (MLJAR, January 19,
    2023), <https://github.com/mljar/mljar-supervised>.

[^9]: Piero Molino, "What Is Ludwig? - Ludwig," accessed January 20,
    2023, <https://ludwig.ai/latest/user_guide/what_is_ludwig/>.
