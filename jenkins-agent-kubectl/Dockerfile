FROM jenkins/jnlp-slave:3.27-1

RUN mkdir -p /home/jenkins/bin
ENV PATH=$PATH:/home/jenkins/bin

ARG KUBECTL
RUN curl -L https://storage.googleapis.com/kubernetes-release/release/v${KUBECTL}/bin/linux/amd64/kubectl -o /home/jenkins/bin/kubectl && \
    chmod +x /home/jenkins/bin/kubectl && \
    kubectl version --client

ARG KUSTOMIZE
RUN curl -L https://github.com/kubernetes-sigs/kustomize/releases/download/v${KUSTOMIZE}/kustomize_${KUSTOMIZE}_linux_amd64 -o /home/jenkins/bin/kustomize && \
    chmod +x /home/jenkins/bin/kustomize && \
    kustomize version

USER root
RUN  apt-get update -y && \
     apt-get install -y git-crypt && \
     rm -rf /var/lib/apt/lists/*
USER jenkins
